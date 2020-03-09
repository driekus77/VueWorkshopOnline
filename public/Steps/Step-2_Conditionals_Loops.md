## Computed values, Conditionals & Loop directives

Computed values allow you to specify a function in the component that does something with the data before it is rendered to the DOM. For instance, you may specify a new property that is the result of adding up or concatenating two other properties, or you may call a function. For example:

```html
<template>
  <div id="example">{{ reversedMessage }}</div>
</template>

<script>
  var vm = new Vue({
    el: "#example",
    data: {
      message: "Hello"
    },
    computed: {
      reversedMessage: function() {
        return this.message
          .split("")
          .reverse()
          .join("");
      }
    }
  });
</script>
```

As you can see, you can use properties in your computed value. You will need this later.

### Conditional: v-if

Conditionals and loops allow us to specify if, and how often, elements in our template are rendered.

The v-if directive specifies a condition that must be met in order for the component on which the directive is placed, to render.

**"v-if"** directive example:

```html
<template>
  <div id="app-3">
    <span v-if="seen">Now you see me</span>
  </div>
</template>
```

Only if the property _seen_ of the component is _true_, will the text be displayed.

### Loop: v-for

The v-for directive can be used to iterate through a collection of values and render the element on which the directive is placed, for every item in the collection.

**"v-for"** directive example:

```html
<template>
  <div id="app-4">
    <ol>
      <li v-for="todo in todos">
        {{ todo.text }}
      </li>
    </ol>
  </div>
</template>

<script>
  var app4 = new Vue({
    el: "#app-4",
    data: {
      todos: [
        { text: "Learn JavaScript" },
        { text: "Learn Vue" },
        { text: "Build something awesome" }
      ]
    }
  });
</script>
```

<i class="far fa-hand-point-down fa-2x"></i>

## Todo(s)

1. Add the days of the month to the monthview.

Hints:

- Use the `getItemsPerMonth` helper function in a computed property.
- Use v-for to iterate through the computed property
- The `getItemsPerMonth` function returns the days in the month in a multiple of 7 items, so you can use a simple flex grid with items of a width of 14% to create a nice month view.

```html
<script>
  import { getItemsPerMonth } from "../helpers";
  ...
</script>
```
