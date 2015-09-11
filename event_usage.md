# InGo Widget Events

----
## Widgets Now Emit Events

As of version x, all InGo widgets now emit events that an implementer can listen for. These events allow you to take action when something happens in the widget to provide the best experience for your registrants and advocates.


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

Now that you know what eveents the InGO widgets emit, you can add code to listen for these events and react to them.

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

## WE NEED MORE DETAIL HERE ON **WHY** A USER WOULD DO THIS!!

### Create a sub emitter for a specific widget 

```js
//Get a sub emitter for a specific widget 
var options = { widgetId: 'WIDGET_ID_HERE', anyparam: ''};
var emitter = InGo.Events.sub(options);
//Suscribe to an event for that widget
emitter.on('EVENT_NAME_HERE', function(args) { ... }) //args include all data in options
```

