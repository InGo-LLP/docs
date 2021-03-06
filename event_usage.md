# InGo Widget Events

----
## Widgets Now Emit Events

All InGo widgets now emit events that an implementer can listen for. These events allow you to take action when something happens in the widget to provide the best experience for your registrants and advocates.


## Types of events

There are many events you can suscribe for each type of widget. Generally these events cover loading, configuring, and rendering of the widget, and the main "action" that that widget performs.  Below is a complete list of the events each of our widgets emits.

### Login widget
- load:started
- load:finished
- config:loaded
- render:started
- render:finished
- manual-authorization:started
- social-authorization:started
- error

### Social widget
- load:started
- load:finished
- config:loaded
- render:started
- render:finished
- social-authorization:started
- social-authorization:finished
- button-invite:clicked
- button-post:clicked
- invitations:sent
- posts:sent
- error

### Confirmation Widget
- load:started
- load:finished
- config:loaded
- confirmation:started
- confirmation:finished

### Registration widget
- load:started
- load:finished
- config:loaded
- form-autocomplete:started
- form-autocomplete:finished
- error

## Listenting and Reacting to Events

Now that you know what eveents the InGO widgets emit, you can add code to listen for these events and react to them. In the following examples, replace 'EVENT_NAME_HERE' with one of the events listed above. The widget ID referenced should be the ID of your unique widget, and must correspond to one of the widgets you've installed in the page.

### Suscribe to events


```js
//Suscribe to an event of a specific widget
InGo.Events.on('EVENT_NAME_HERE', function(args) { ... }, ['WIDGET_ID_HERE'])
```

```js
//Suscribe to an event for a set of widgets
InGo.Events.on('EVENT_NAME_HERE', function(args) { ... }, ['WIDGET_1_ID_HERE', 'WIDGET_2_ID_HERE', ..., 'WIDGET_N_ID_HERE'])
```

```js
//Suscribe to an event for all widgets
InGo.Events.on('EVENT_NAME_HERE', function(args) { ... })
```

### Suscribe to an event only once

```js
//Suscribe once to an event of a specific widget
InGo.Events.once('EVENT_NAME_HERE', function(args) { ... }, ['WIDGET_ID_HERE'])
```

```js
//Suscribe once to an event for a set of widgets
InGo.Events.once('EVENT_NAME_HERE', function(args) { ... }, ['WIDGET_1_ID_HERE', 'WIDGET_2_ID_HERE', ..., 'WIDGET_N_ID_HERE'])
```

```js
//Suscribe once to an event for all widgets
InGo.Events.once('EVENT_NAME_HERE', function(args) { ... })
```

### Unsuscribe from an event

```js
//Unsuscribe from an event of a specific widget
InGo.Events.off('EVENT_NAME_HERE', function(args) { ... }, ['WIDGET_ID_HERE'])
```

```js
//Unsuscribe from an event for a set of widgets
InGo.Events.off('EVENT_NAME_HERE', function(args) { ... }, ['WIDGET_1_ID_HERE', 'WIDGET_2_ID_HERE', ..., 'WIDGET_N_ID_HERE'])
```

```js
//Unsuscribe from an event for all widgets
InGo.Events.off('EVENT_NAME_HERE', function(args) { ... })
```

### Subscribing to More Than One Event Using a Sub Emitter

If you need to suscribe to more than one event for the same widget, you can optionally create a sub emitter using the widget id. With the sub emitter you can suscribe or unsuscribe to event(s) produced by the widget without the need to pass the widget id every time. You can also pass data in the option parameter. Any data in the option parameter will be received in the args parameter of the callback function you provide.

In case you need to suscribe to more than one event for the same widget, you can create a sub emitter using the widget id. With the sub emitter you can suscribe or unsuscribe to whatever event of the widget that you want and you do not need to pass the widget id everytime. Moreover, any field that you pass in the option parameter, will be received in the args parameter of the callback function.

```js
//Get a sub emitter for a specific widget 
var options = { widgetId: 'WIDGET_ID_HERE', anyparam: ''};
var emitter = InGo.Events.sub(options);
//Suscribe to many events for that widget
emitter.on('EVENT_NAME_HERE', function(args) { ... }) //args include all data in options
emitter.on('EVENT_2_NAME_HERE', function(args) { ... }) 
```

