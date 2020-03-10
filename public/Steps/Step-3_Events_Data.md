## Events & Data

### Listening to events

You can use the _v-on_ directive to bind to events. The example below listens to the click event:

```html
<div>
  <button v-on:click="counter += 1">Add 1</button>
  <p>The button above has been clicked {{ counter }} times.</p>
</div>
```

You can also bind the event to a component method:

```html
<template>
  <div v-on:click="greet">Click here.</div>
</template>

<script>
  export default {
    name: "MyComponent",
    methods: {
      greet: function(event) {
        alert("Hello!");
      }
    }
  };
</script>
```

### Emitting events

Components can also emit events by calling the `this.$emit(name)` method. The parent component can then listen to this event using `v-on:name`.

The value for name can be freely chosen by the developer. However, remember that the HTML DOM is case-insensitive and therefor Vue.js always converts event names to lowercase. In other words, `v-on:myEvent` becomes `v-on:myevent` – making `this.$emit('myEvent')` impossible to listen to.

You can also include an extra parameter when emitting an event:

```javascript
this.$emit("myevent", value);
```

This parameter can be retrieved in the event handler in the \$event variable:

```html
<MyComponent v-on:myevent="alert($event)"></MyComponent>
```

<i class="far fa-hand-point-down fa-2x"></i>

## Todo(s)

### 1. Bind a method to the click event of a day in the _MonthView_ component

- Create a method in the component
- Bind the method to a click event
- Update the selected date in the component state

Hint: for this, we will need to add state to our component:

```html
<script>
  export default {
    name: "MonthView",
    props: {
      year: Number,
      month: Number
    },
    data: function() {
      return {
        selectedDate: null
      };
    }
  };
</script>
```

You can reference the component state in your method using `this.selectedDate`.

- Create a style class and add it to the selected date, so the user can see which date is selected.

Hint: in properties, you do not need to include `this` when referencing state.

### 2. Create a new component for showing appointments

- Create a component called _Appointments.vue_
- Add the component to the _Agenda_ component.

### 3. Let the _Appointments_ component show the selected date

- Emit a _selecteddatechanged_ event up from the _MonthView_ component to the _Agenda_ component. Hint: do not pass the moment.js object in the event, but a javascript Date (a moment.js object can be converted to a javascript date using the `.toDate()` method).
- Store the selected date in the state of the agenda component
- Add a date property to the _Appointments_ component and set it from the _Agenda_ component
