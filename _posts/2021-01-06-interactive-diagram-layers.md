---
layout: post
author: draw.io
slug: interactive-diagram-layers
date: 2021-01-06 09:10:00
title: Create an interactive diagram and toggle layers with custom links
tags: [features]
categories: [features]
---

Complex diagrams can be made a lot easier to read and understand when you split them up into logical smaller diagrams on multiple pages, or by using a number of layers. 
<br /><img src="/assets/img/blog/interactive-diagram-toggle-editor.gif" style="width=100%;max-width:400px;height:auto;;" alt="Paste the custom link into the first text field and click Apply">

To learn more about the complex diagram, you can toggle the display of layers and step to another diagram page using the toolbar at the bottom of the diagram viewer, or the layers dialog and page tabs in the diagram editor. 

Alternatively, you can make your diagram interactive by adding custom links to the shapes and text within the diagram that act as intuitive toggle switches - you don't have to use the toolbar to interact with your diagram.

Diagrams that can benefit from adding interactive layers _within the diagram itself_ include [network or infrastructure diagrams](/blog/network-diagrams.html), [floor plans](/blog/floorplans.html) and [gitflow diagrams](/blog/gitflow-diagram.html). 

[Learn more about using layers in draw.io](/doc/layers.html)

<img src="/assets/img/blog/interactive-diagram-viewer-toolbar.png" style="max-width:100%;height:auto;" alt="Step through the pages and interact with layers in the draw.io online viewer">

## Use custom links to add interactivity

Custom links are small pieces of JSON code containing the shape or layer IDs of the diagram elements you want to make interactive. 

You can ``open`` a web URL or custom link, ``toggle`` elements on or off, ``show``, ``hide``, or ``highlight`` diagram elements, ``select`` elements, ``scroll`` to a specific element in the diagram, or set a ``viewbox`` with a custom link. 

For example, the following JSON action in a custom link toggles the display of a layer - it hides it if it is visible, or displays it if it is hidden.

```data:action/json,{"actions":[{"toggle":{"cells":["YwLYfkWT0Qeqm7Gh2uLp-177"]}}]}```

[Learn more about custom links](/doc/faq/custom-links.html)

**An example interactive gitflow diagram**

In the example below, interactive layer ``toggle`` switches will be added to the gitflow diagram to let you click on the following labels and display or hide their branches.
* Release and Release Fix
* Feature team 1 and their development branches
* Feature team 2 and their development branches

The Master, Nightly, and Hotfix branches, and the Development label are always displayed, and therefore placed on the background layer.

_[Open the interactive gitflow example in our online diagram viewer](https://viewer.diagrams.net/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&page=1&nav=1&title=#Uhttps%3A%2F%2Fraw.githubusercontent.com%2Fjgraph%2Fdrawio-diagrams%2Fdev%2Fblog%2Fgitflow-interactive-custom-links.drawio)_


### Set up shapes to use as toggle switches

When you click on a shape that is used as a toggle and it exists on the layer or in the group that you want to hide, you won't be able to click on it again. 

1. Make a copy of the shapes you want to use as toggles, and paste them onto the _Background_ layer.
2. Position them directly under the original shapes on the other layers so that when you click, diagram elements don't appear to move position.
<br /><img src="/assets/img/blog/interactive-diagram-add-toggle-shapes-background.png" style="width:100%; max-width:400px;height:auto;" alt="Add a copy of the shapes you want to use as toggles to the background layer in your diagram">

### Copy the layer ID

1. Select _View > Layers_ or press ``Ctrl+Shift+L`` / ``Cmd+Shift+L`` to display the _Layers_ dialog if you don't see it.
2. Select a layer, then in the Layers dialog menu (three horizontal bars), select _Current Layer > Edit Data_. 
<br /><img src="/assets/img/blog/interactive-diagram-get-layer-id.png" style="width:100%; max-width:200px;height:auto;" alt="Edit the metadata of the layer to find its layer ID">
1. Copy the layer _ID_ - the long string of numbers and letters. 
<br /><img src="/assets/img/blog/interactive-diagram-get-layer-id2.png" style="width:100%; max-width:400px;height:auto;" alt="Copy the layer ID so you can build a custom link">

**Tip:** If you want to toggle a single shape instead of a layer, press ``Ctrl+M`` or ``Cmd+M`` to edit the shape's metadata, then copy its _ID_ (a short number).

### Build the custom link

1. Go to [the draw.io utility tools page](https://jgraph.github.io/drawio-tools/tools/link.html).
2. Paste the layer ID into the _Cells/Layers_ text field. You can toggle more than one layer or shape in a custom link - add all of their shape/layer IDs separated by a space.
3. Click on _5. Add Action_ to generate the _Custom Link_ in the larger text field below. 
4. Click on _Copy Link_ to copy the _Custom Link_.
<br /><img src="/assets/img/blog/interactive-diagram-build-custom-link.png" style="max-width:100%;height:auto;" alt="Paste the shape and layer IDs, generate the custom link, then copy it to the clipboard using this free tool">

### Add the custom link to a shape
1. Back in the draw.io editor, right-click on a shape in your diagram, then select _Edit Link_, or select the shape and use the keyboard shortcut ``Alt+Shift+L``.
<br /><img src="/assets/img/blog/interactive-diagram-edit-shape-link.png" style="width:100%; max-width:200px;height:auto;" alt="Edit the shape's metadata to add the custom link">
2. Enter the custom link in the first text field, then click _Apply_.
<br /><img src="/assets/img/blog/interactive-diagram-add-custom-link.png" style="width:100%; max-width:400px;height:auto;" alt="Paste the custom link into the first text field and click Apply">
3. Make sure you add the same link to the matching shape on the Background layer so you can toggle the layer back on again.

## Interact with your diagram

When you view the diagram in the editor, you can interact with your diagram in three ways:

* Click on the checkbox in the the _Layers_ dialog. 
* If the layer you toggle is locked, click directly on the shape in the same way as if you are interacting with the diagram in the viewer. 
* If the layer is unlocked, the custom link is shown in a tooltip with the label ``Action`` when you select the shape. Click on this link to display or hide your layers and shapes.

<img src="/assets/img/blog/interactive-diagram-toggle-editor.gif" style="max-width:100%;height:auto;" alt="Paste the custom link into the first text field and click Apply">

_[Open this interactive gitflow in our diagram viewer](https://viewer.diagrams.net/?lightbox=1&highlight=0000ff&edit=_blank&layers=1&page=1&nav=1&title=#Uhttps%3A%2F%2Fraw.githubusercontent.com%2Fjgraph%2Fdrawio-diagrams%2Fdev%2Fblog%2Fgitflow-interactive-custom-links.drawio)_

