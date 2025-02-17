# Event

LogicFlow provides an event system to inform the developer of events that occur in the current flowchart. The detailed usage of events is described in [Events](en/guide/basic/event).

## Node Events

| Event names           | Description                   | Event object         |
| :--------------- | :--------------------- | :---------------- |
| element:click    | Click on the element               | data, e, position |
| node:click       | Click on the node               | data, e, position |
| node:dbclick     | Double-click on the node              | data, e, position |
| node:mousedown   | Mouse down node           | data, e           |
| node:mouseup     | Mouse up node           | data, e           |
| node:mousemove   | Mouse move node           | data, e           |
| node:mouseenter  | Mouse enter node           | data, e           |
| node:mouseleave  | Mouse leave node            | data, e           |
| node:delete      | Delete node             | data              |
| node:add         | Add node            | data              |
| node:dnd-add     | When a node is dragged in from outside, the node added will trigger the event | data              |
| node:dnd-drag    | When a node is dragged in from outside, the node in the dragged state will trigger the event | data              |
| node:dragstart   | Start dragging nodes           | data, e           |
| node:drag        | Nodes in dragging               | data, e           |
| node:drop        | End of node dragging           | data, e           |
| node:contextmenu | Right-click on the node           | data, e, position |

The event object contains the following:

| Properties     | Type       | Description                                                                                                  |
| :------- | :--------- | :-------------------------------------------------------------------------------------------------- |
| data     | Object     | The [data attribute](en/api/nodeModelApi#DataAttributes) of the node                                                     |
| e        | MouseEvent | Native mouse event object                                                                                  |
| position | Object     | Coordinates of the mouse trigger point in the canvas(Refer to the return value of [getPointByClient](en/api/logicFlowApi#getpointbyclient) |

## Edge Events

| Event names                 | Description              | Event object          |
| :--------------------- | :---------------- | :---------------- |
| element:click          | Click on the element          | data, e, position |
| edge:click             | Click on the edge            | data, e, position |
| edge:dbclick           | Double-click on the edge            | data, e           |
| edge:mouseenter        | Mouse enter edge        | data, e           |
| edge:mouseleave        | Mouse leave edge        | data, e           |
| edge:add               | Add edge            | data              |
| edge:delete            | Delete edge            | data              |
| edge:contextmenu       | Right-click on the edge            | data, e, position |
| edge:adjust            | Drag to adjust the edge        | data              |
| edge:exchange-node     | Adjust the start/end of the edge | data              |
| connection:not-allowed | Connection not allowed    | data, msg         |

The event object contains the following:

| Properties     | Type       | Description                                                                                                  |
| :------- | :--------- | :-------------------------------------------------------------------------------------------------- |
| data     | Object     | The [data attribute](en/api/edgeModelApi#DataAttributes) of the edge                                                      |
| e        | MouseEvent | Native mouse event object                                                                                  |
| position | Object     | Coordinates of the mouse trigger point in the canvas(Refer to the return value of [getPointByClient](en/api/logicFlowApi#getpointbyclient) |
| msg      | String     | Verification information of the edge                                                                                         |

## Anchor Events

| Event names           |Description                                                                                                    | Event object                     |
| :--------------- | :------------------------------------------------------------------------------------------------------ | :---------------------------- |
| anchor:dragstart | Start connecting based on anchor points                                                                                        | data, e, nodeModel            |
| anchor:drop      | Manual connection success based on anchor points. Triggered only if the edge is created successfully. Used to distinguish between manually created edges and automatically created edges (`edge:add`) | data, e, nodeModel, edgeModel |
| anchor:dragend   | End of manual connection based on anchor points. This is triggered whether or not the edge is successfully created.                                                                | data, e, nodeModel            |

The event object contains the following:

| Properties      | Type       | Description                 |
| :-------- | :--------- | :----------------- |
| data      | Object     | Anchor data           |
| e         | MouseEvent | Native mouse event object |
| nodeModel | Object     | The node to which the anchor point belongs     |

## Graph Events

| Event names            | Description                                                                       | Event object    |
| :---------------- | :------------------------------------------------------------------------- | :---------- |
| blank:mousedown   | Mouse down on the canvas                                                               | e           |
| blank:mousemove   | Mouse move on the canvas                                                               | e           |
| blank:mouseup     | Mouse up on the canvas                                                              | e           |
| blank:click       | Click on the canvas                                                                    | e           |
| blank:contextmenu | Right-click on the canvas                                                                   | e, position |
| blank:dragstart   | Start dragging canvas                                                               | e           |
| blank:drag        | Canvas in dragging                                                                   | e           |
| blank:drop        | End of canvas dragging                                                               | e           |
| text:update       | Update text                                                                   | data        |
| graph:transform   | Triggered when panning or zooming the canvas                                                       | data        |
| graph:rendered    | Triggered after the canvas renders data, i.e. after the lf.render(graphData) method is called. `Add in v1.1.0` | graphData   |

The event object contains the following:

| Properties     | Type       | Description                                                                                                  |
| :------- | :--------- | :-------------------------------------------------------------------------------------------------- |
| e        | MouseEvent | Native mouse event object                                                                                  |
| position | Object     | Coordinates of the mouse trigger point in the canvas(Refer to the return value of [getPointByClient](en/api/logicFlowApi#getpointbyclient) |

## History Events

History is used to record every change on the canvas. The `history:change` event is triggered when an element on the canvas changes.

| Event names         | Description     | Event object |
| :------------- | :------- | :------- |
| history:change | The canvas changes | data     |

The data property in the event object contains the following content:

| Properties     | Type    | Description                |
| :------- | :------ | :------------------ |
| undos    | Array   | Undoable graph snapshots |
| redos    | Array   | Redoable graph snapshots |
| undoAble | Boolean | Whether it can be undone        |
| redoAble | Boolean | Whether it can be redone       |

## Selection Events

Events triggered when multiple nodes are selected at the same time to form a selection.

| Event names                | Description           | Event object       |
| :-------------------- | :------------- | :------------- |
| selection:selected    | Triggered when the selection is selected | All selected elements |
| selection:mousedown   | Mouse down on the selection   | e              |
| selection:dragstart   | Start dragging the selection   | e              |
| selection:drag        | Selection in dragging       | e              |
| selection:drop        | End of selection dragging   | e              |
| selection:mousemove   | Move the mouse on the selection   | e, position    |
| selection:mouseup     | Release the mouse on the selection   | e              |
| selection:contextmenu | Right-click on the selection       | e              |

The event object contains the following:

| Properties     | Type       | Description                                                                                                  |
| :------- | :--------- | :-------------------------------------------------------------------------------------------------- |
| e        | MouseEvent | Native mouse event                                                                                  |
| position | Object     | Coordinates of the mouse trigger point in the canvas(Refer to the return value of [getPointByClient](en/api/logicFlowApi#getpointbyclient) |

## on

Register events.

Parameters:

| Name    | Type  | Required | Default | Description     |
| :------- | :----- | :--- | :----- | :------- |
| evt      | String | ✅   | -      | Event Name |
| callback | String | ✅   | -      | Callback function |

Example:

```js
const { eventCenter } = lf.graphModel;

eventCenter.on("node:click", (args) => {
  console.log("node:click", args.position);
});
eventCenter.on("element:click", (args) => {
  console.log("element:click", args.e.target);
});
```

## off

Delete registered events.

Parameters:

| Name     | Type   | Required | Default | Description     |
| :------- | :----- | :--- | :----- | :------- |
| evt      | String | ✅   | -      | Event Name |
| callback | String | ✅   | -      | Callback function |

Example:

```js
const { eventCenter } = lf.graphModel;
eventCenter.off("node:click", () => {
  console.log("node:click off");
});
eventCenter.off("element:click", () => {
  console.log("element:click off");
});
```

## once

The event are triggered only once.

Parameters:

| Name    | Type   | Required | Default | Description    |
| :------- | :----- | :--- | :----- | :------- |
| evt      | String | ✅   | -      | Event Name |
| callback | String | ✅   | -      | Callback function |

Example:

```js
const { eventCenter } = lf.graphModel;

eventCenter.once("node:click", () => {
  console.log("node:click");
});
```

## emit

Trigger the event.

Parameters:

| Name | Type   | Required | Default | Description         |
| :--- | :----- | :--- | :----- | :----------- |
| evt  | String | ✅   | -      | Event Name     |
| args | Array  | ✅   | -      | Callback function |

Example:

```js
const { eventCenter } = lf.graphModel;
eventCenter.emit("custom:button-click", data);
```
