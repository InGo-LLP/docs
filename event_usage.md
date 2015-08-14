# InGo Widget Events

----

## How to suscribe to events

### Suscribe to an event of a specific widget

```js
//Single widget event suscription
InGo.on('EVENT_NAME_HERE', 'WIDGET_ID_HERE', function(args) { ... })
```

### Suscribe to an event for a set of widgets

```js
//Set of widget event suscription
InGo.on('EVENT_NAME_HERE', 'WIDGET_1_ID_HERE', 'WIDGET_2_ID_HERE', ..., 'WIDGET_N_ID_HERE', function(args) { ... })
```

### Suscribe to an event for all widgets

```js
//All widgets event suscription
InGo.on('EVENT_NAME_HERE', function(args) { ... })
```

## Types of events

There are many events you can suscribe for each type of widget.

### Login widget
- load
- render

### Social widget
- load
- render

### Registration Widget
- load

### Confirmation widget
- load
