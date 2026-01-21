---
title: Work with layers in draw.io
layout: page
faq: true
categories: [Features]
---

Layers add structure and organisation to your diagrams. When you interact with a complex diagram, to display or hide its various layers, you can understand them more easily.

**Note:** Each shape or connector (or group) can only be placed on one layer - it can't belong to multiple layers.

## Using layers in diagrams

The sections below explain how to work with layers in draw.io.

- [Using layers in diagrams](#using-layers-in-diagrams)
  - [Open the Layers dialog](#open-the-layers-dialog)
  - [Add a new layer](#add-a-new-layer)
  - [Rename a layer](#rename-a-layer)
  - [Remove a layer](#remove-a-layer)
- [Work with shapes on layers](#work-with-shapes-on-layers)
  - [Add shapes to a layer](#add-shapes-to-a-layer)
  - [See which layer a shape belongs to](#see-which-layer-a-shape-belongs-to)
  - [Move shapes to another layer](#move-shapes-to-another-layer)
  - [Rearrange layers to move shapes forward or backward](#rearrange-layers-to-move-shapes-forward-or-backward)
- [Hide or display layers](#hide-or-display-layers)
- [Lock layers to prevent changes](#lock-layers-to-prevent-changes)
- [Select objects in a layer](#select-objects-in-a-layer)
- [Diagrams that work well with layers](#diagrams-that-work-well-with-layers)

**Tip:** [Open the example gitflow in the draw.io editor](https://app.diagrams.net/?lightbox=0&highlight=0000ff&edit=_blank&layers=1&page=0&nav=1&title=#Uhttps%3A%2F%2Fraw.githubusercontent.com%2Fjgraph%2Fdrawio-diagrams%2Fdev%2Fblog%2Fgitflow-layers.drawio) - use the sections below to learn how to work with these layers in a diagram. 

You can also learn [how the ``.drawio`` file format works with layers](/blog/how-layers-work.html)

### Open the Layers dialog

Select _View > Layers_ or press ``Ctrl+Shift+L`` / ``Cmd+Shift+L`` to display or hide the _Layers_ dialog.

<img src="/assets/img/blog/view-layers.png" style="max-width:100%;height:auto;" alt="Select View > Layers to open the Layers dialog">

By default, a new diagram has a single _Background_ layer, to which all shapes, connectors and text are added.

From the Layers dialog, you can add new layers and rename them, select which layer to add new shapes to, remove existing layers, and move selected shapes to a layer. 

You can also display and hide layers, which will display or hide all the shapes, connectors and text that are on those layers. 

Finally, locking a layer makes sure you can't make any inadvertent changes.

### Add a new layer 

At the bottom of the _Layers_ dialog, click on _Add Layer_ (``+``). 

Your new layer will be automatically selected (with a blue background), and any new shapes you add to the drawing canvas will be placed on your new layer.

<img src="/assets/img/blog/layer-add.png" style="max-width:100%;height:auto;" alt="Click on Add Layer (+) in the Layers dialog to add a new layer">

**Duplicate a layer:** Select the layer you want to duplicate, then click on the Layers menu (three horizontal lines) and select _Current Layer > Duplicate_.

<img src="/assets/img/blog/layer-duplicate.png" style="width=100%;max-width:300px;height:auto;" alt="Select a layer then click on Duplicate (overlapping box) in the Layers dialog to duplicate it">

[_Back to top_](#using-layers-in-diagrams)

### Rename a layer

When you add a new layer, it will be given a default name. Start typing immediately to change its name to something meaningful. Double click on any layer to edit its new name at any time, or open the Layers menu and select _Current Layer > Rename_.

<img src="/assets/img/blog/layer-rename.png" style="width=100%;max-width:400px;height:auto;" alt="Double click on a layer, and enter a new name">

**Rename a layer via its metadata**

Layers have metadata, just like shapes have metadata. This metadata allowed advanced functionality within your You can also change a layer's name via the _Edit Data_ dialog.

[See how to use metadata and placeholders in labels and tooltips](/blog/placeholders.html)

1. Select a layer, then click on the Layers menu (three horizontal bars) and select _Current Layer > Edit Data_. 
<br /><img src="/assets/img/blog/layer-edit-data.png" style="width=100%;max-width:300px;height:auto;" alt="Select a layer in the Layers dialog, then click on Edit Data">
1. Change the text in the _Label_ field and click _Apply_ to change the layer's name.
<br /><img src="/assets/img/blog/layer-edit-data-dialog.png" style="width=100%;max-width:300px;height:auto;" alt="In the Edit Data dialog for that layer, change the label text and click Apply to rename it">

[_Back to top_](#using-layers-in-diagrams)

### Remove a layer

Removing a layer will delete all the shapes and connectors that are on it as well as the layer itself. Click on a layer to select it, then click on _Delete_ in the bottom of the _Layers_ dialog (rubbish bin) to remove the layer and its shapes.

<img src="/assets/img/blog/layer-remove.png" style="width=100%;max-width:250px;height:auto;" alt="Select a layer, then click on the rubbish bin icon to remove it and all the shapes/connectors it contains">

**Note:** Your diagram must have at least one layer for shapes and connectors to be placed. If there is only one layer in your diagram, you can not delete it. 

[_Back to top_](#using-layers-in-diagrams)

## Work with shapes on layers

Shapes are arranged in the order you added them to the drawing canvas, within the layer you added them. 

Layers are arranged from front to back as they are ordered top to bottom in the _Layers_ dialog. Shapes and connectors placed on a higher layer can not go behind shapes on a lower layer - they can only be arranged from front to back _within their layer_.

### Add shapes to a layer 

1. Make the layers are visible and unlocked before you make changes (click on the eye to display a hidden layer and the lock icon to the left of the layer name). Layers are unlocked by default.
2. Select the layer you want to add the shape to in the _Layers_ dialog, then add the shape to the drawing canvas. 

<img src="/assets/img/blog/layer-add-shape.gif" style="max-width:100%;height:auto;" alt="Make the layer you want to add the shape or connector to visible and unlocked, then select it, and add your shape/connector">

[_Back to top_](#using-layers-in-diagrams)

### See which layer a shape belongs to

Select one shape or more shapes - make sure they are all on the same layer. Note the dot to the right of the layer name - this shows that your selected shape(s) are on that layer. 

<img src="/assets/img/blog/shape-find-layer.png" style="max-width:100%;height:auto;" alt="Select a shape, note the dot on the right of the layer name - this is the layer the shape belongs to">

**Note:** If you have selected shapes on different layers, you will not see a dot in the Layers dialog.

[_Back to top_](#using-layers-in-diagrams)

### Move shapes to another layer

1. Select the shapes, connectors and text you want to move to another layer. 
2. In the layers dialog, click on the three horizontal lines (Layers Menu), then _Move Selection to_ and click on the layer you want to move your selected shapes to.

<img src="/assets/img/blog/shapes-move-layers.png" style="max-width:100%;height:auto;" alt="Move the selected shapes to another layer via the Layers dialog">

The dot indicating on which layer your selected shapes are will be updated to your choice.

[_Back to top_](#using-layers-in-diagrams)

### Rearrange layers to move shapes forward or backward

To move one layer's shapes in front of another, you need to change the order of the layers in the _Layers_ dialog. Layers are arranged from top to bottom (front to back on the drawing canvas).

[Learn how the z-order of shapes positions them in front of or behind other shapes](/blog/move-shapes-forwards-backwards.html)

Click and drag a layer in the _Layers_ dialog to place its shapes in front of or behind another layer.

<img src="/assets/img/blog/layer-rearrange.gif" style="max-width:100%;height:auto;" alt="In the Layers dialog, drag a layer higher or lower to move its contents above or below shapes and connectors on the other layers">

**Note:** When you move shapes to a layer, they are placed in front of any existing shapes on that layer, just like when you add new shapes to a layer.

Alternatively, select a layer, open the Layers dialog menu, click on _Current Layer_ and choose to move the layer forwards or backwards. 
<img src="/assets/img/blog/layers-z-order.png" style="width=100%;max-width:500px;height:auto;" alt="Move the selected layer in front or or behind other layers via the Layers dialog">
<br />[_See how layers work with z-order in draw.io_](/blog/how-layers-work.html)

[_Back to top_](#using-layers-in-diagrams)

## Hide or display layers

To understand complex diagrams that use layers, you can display and hide layers. 

In the _Layers_ dialog, click on the eye on the left of layer's name to display or hide the layer.

<img src="/assets/img/blog/layers-display-hide.gif" style="max-width:100%;height:auto;" alt="Click on the eye next to the layer name to display or hide the shapes and connectors on that layer">

**Hide or display layers in the diagram viewer:** Click on the _Layers_ tool at the bottom of the diagram viewer, then click on the eye icons next to the layer names to hide or display the layers. This tool is not available if the diagram only has one layer.

<img src="/assets/img/blog/layers-viewer-display-hide.png" style="max-width:100%;height:auto;" alt="Click on the layer tool then on the eyes next to layer names to hide or display them in the diagram viewer">

**Tip:** [Use custom links to make your diagram interactive](/blog/interactive-diagram-layers.html) and toggle layers on and off when you click on a shape within the diagram. 

[_Back to top_](#using-layers-in-diagrams)

## Lock layers to prevent changes

Locking a layer means you cannot make any changes to it - you can't add, move, edit, style or delete the shapes and connectors placed on that layer. 

In the _Layers_ dialog, click on the padlock icon to the left of the layer's name that you want to lock.

<img src="/assets/img/blog/layer-locked-add-shape-failure.gif" style="max-width:100%;height:auto;" alt="Click on the padlock next to a layer's name in the Layers dialog to lock or unlock the layer">

[_Back to top_](#using-layers-in-diagrams)

## Select objects in a layer

1. Select a layer in the Layers dialog. 
2. In the Layers dialog menu, select _Current Layer > Select Objects in Layer_. 

This does not select shapes and connectors inside any container shapes or groups in that layer. In the example below the Container shapes and brackets in the Service layer are selected, but the shapes inside those containers are not. They will still move and be copied along with their container. 

<img src="/assets/img/blog/layers-select-objects-in-layer.png" style="width=100%;max-width:500px;height:auto;;" alt="Select the objects in the current layer selects any container shapes or groups, but does not select any objects inside those containers/groups">

See [how layers, shapes and connectors are organised](/blog/how-layers-work.html) inside the ``.drawio`` diagram format.

## Diagrams that work well with layers

* [Floor plans](/blog/floorplans.html) - Add furniture, appliances or IT devices, fixtures, and decorations on separate layers.
* [Network diagrams](/blog/network-diagrams.html) - Place areas behind firewalls or on different subnets on different layers. 
* [Gitflow diagrams](/blog/gitflow-diagram.html) - Separate team or feature branches onto their own layers. Open this [example gitflow diagram with layers](https://viewer.diagrams.net/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&page=0&nav=1&title=#Uhttps%3A%2F%2Fraw.githubusercontent.com%2Fjgraph%2Fdrawio-diagrams%2Fdev%2Fblog%2Fgitflow-layers.drawio) in the lightbox viewer.