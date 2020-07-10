---
title: Widget to Image
parent: Flutter
---

# Widget to Image

In this post we will be building a simple app that captures the current state of a widget into an image.

---

Capturing a widget into an image is nothing too hard using the [toImage](https://master-docs-flutter-io.firebaseapp.com/flutter/rendering/RenderRepaintBoundary/toImage.html) method provided by the `RenderRepaintBoundary` class, but there is a catch. To use the `toImage` method, the widget must have already gone through the paint phase. We will find a workaround to allow you to capture a widget while it is offscreen.
## Creating the UI

```dart
class HomePage extends StatefulWidget {
  HomePage({Key key}) : super(key: key);

  @override
  _HomeState createState() => _HomeState();
}

class _HomeState extends State<HomePage> {
  GlobalKey globalKey = GlobalKey(); // We will need the key to get the render object

  @override
  Widget build(BuildContext context) {
    return RepaintBoundary(
      key: globalKey,
      child: Center(
        child: FlatButton(
          child: Text('Henlo birb!'),
          onPressed: _captureImage, 
        ),
      ),
    );
  }
}
```

This should give you a simple app with a `FlatButton` that says "Henlo Birb" in the center of your screen.

RepaintBoundary creates a widget that isolate repaints. Containing `RenderObject.paint` to parts of the render subtree that are actually visually changing minimizes redundant work.

## Capturing the image

You may have noticed that we placed a `_captureImage` method in the `FlatButton`'s onPressed callback, but we haven't implemented it.
The method is as simple as finding the widget's RenderObject and calling the `toImage` method on it. For the sake of it we capture the image as a png.

```dart
Future<void> _captureImage() async {
  RenderRepaintBoundary boundary = globalKey.currentContext.findRenderObject();
  ui.Image image = await boundary.toImage();
  ByteData byteData = await image.toByteData(format: ui.ImageByteFormat.png);
  Uint8List pngBytes = byteData.buffer.asUint8List();
  print(pngBytes);
}
```

You can write pngBytes to a file using the `writeAsBytes` or `writeAsBytesSync` methods, but this is enough to demonstrate how it works.

## Capture Without Painting on Screen

There are many widgets like `Offstage`, but the majority of them only lay out the child but do not paint it. A possible workaround for this would be to create a separate `PipelineOwner` and `BuildOwner`. The `PipelineOwner` would allow us to manage a separate render tree, while the `BuildOwner` allows us to manage a separate element tree.

With that we could inflate the tree and flush the pipeline to paint the widgets offscreen and call the `toImage` method.

To flush the pipeline we have to call the following functions in order:
    
  1. `flushLayout` - updates any render objects that need to compute their layouts.
  2. `flushCompositingBits` - updates any render objects that have dirty compositing bits.
  3. `flushPaint` - visits any render objects that need to paint.
  4. ***Only if semantics are enabled*** - `flushSemantics` - compiles the semantics for the render objects.
    
```dart
Future<Uint8List> widgetToImage(Widget widget) async {
  final RenderRepaintBoundary repaintBoundary = RenderRepaintBoundary();

  var logicalSize = ui.window.physicalSize / ui.window.devicePixelRatio;
  var imageSize = ui.window.physicalSize;

  final RenderView renderView = RenderView( // a RenderView is the root of a render tree
    window: null, // pass null since we don't want it to paint onscreen
    child: RenderPositionedBox(alignment: Alignment.center, child: repaintBoundary),
    configuration: ViewConfiguration(
      size: logicalSize,
      devicePixelRatio: 1.0,
    ),
  );

  final PipelineOwner pipelineOwner = PipelineOwner(); // allows us to manage a separate render tree
  final BuildOwner buildOwner = BuildOwner(); // allows us to manage a separate element tree

  pipelineOwner.rootNode = renderView; // attach renderView as the root node. A root node is a unique object without a parent.
  renderView.prepareInitialFrame(); // Doesn't schedule the first frame

  final RenderObjectToWidgetElement<RenderBox> rootElement = RenderObjectToWidgetAdapter<RenderBox>(
    container: repaintBoundary,
    child: widget,
  ).attachToRenderTree(buildOwner);

  buildOwner.buildScope(rootElement); // Creates a scope for updating the widget tree and call the given callback (if given) and finally build any dirty elements

  buildOwner.buildScope(rootElement);
  buildOwner.finalizeTree();

  // Flushing the pipeline
  pipelineOwner.flushLayout();
  pipelineOwner.flushCompositingBits();
  pipelineOwner.flushPaint();

  // Convert to an image and return the bytes as a png format
  final ui.Image image = await repaintBoundary.toImage(pixelRatio: imageSize.width / logicalSize.width);
  final ByteData byteData = await image.toByteData(format: ui.ImageByteFormat.png);

  return byteData.buffer.asUint8List();
}

```

We can now pass widgets to this method, and use the returned bytes to create a file.

```dart
final exampleWidget = MaterialApp(
  home: Scaffold(
    body: Container(
      child: Center(child: Text("Henlo Birb!")),
    ),
  ),
);

var bytes = await widgetToImage(exampleWidget);
print(bytes);
```




