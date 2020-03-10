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

### Conditional attributes

In Vue.js, you can also use conditions in attributes by using the v-bind directive to bind the DOM attribute to a component property:

```html
<div v-bind:class="{ active: isActive }">
  Element active: {{ isActive }}
</div>
```

Note: you can also abbreviate (shorthand) v-bind as follows:

```html
<div :class="{ active: isActive }">
  Element active: {{ isActive }}
</div>
```

And you can also combine standard attributes and bound ones:

```html
<div class="element" :class="{ active: isActive }">
  Element active: {{ isActive }}
</div>
```

### Loop: v-for

The v-for directive can be used to iterate through a collection of values and render the element on which the directive is placed, for every item in the collection.

**"v-for"** directive example:

```html
<template>
  <div id="app-4">
    <ol>
      <li :key="todo.id" v-for="todo in todos">
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
        { id: 1, text: "Learn JavaScript" },
        { id: 2, text: "Learn Vue" },
        { id: 3, text: "Build something awesome" }
      ]
    }
  });
</script>
```

Note that, when creating elements in a loop, every (root) element you create requires a unique key, just as in Angular and React.

<i class="far fa-hand-point-down fa-2x"></i>

## Todo(s)

### 1. Create a _computed property_ that gets the name of the month.

- Use the `getFullMonthName` helper function in a _computed property_ named _monthName_. The `getFullMonthName` function can be found in helpers.js and expects a single parameter: month.
- Display the month name in the header of your component.

### 2. Add the days of the month to the monthview.

Hints:

- Use the `getItemsPerMonth` helper function in a _computed property_. The `getItemsPerMonth` function can be found in helpers.js and expects two parameters: year and month.

```html
<script>
  import { getItemsPerMonth } from "../helpers";
  ...
</script>
```

- Use v-for to iterate through the computed property
- The `getItemsPerMonth` function returns the days in the month in a multiple of 7 items (a week), starting on monday, so you can use a simple flex grid with items of a width of 14% to create a nice month view. You may copy the style below if you like:
- The objects returned by `getItemsPerMonth` have a date property which is a moment.js date. You can get the day of the month as follows: `item.date.date()`

```html
<style>
  .month {
    display: flex;
    flex-wrap: wrap;
  }

  .day {
    width: 14%;
    height: 2em;
    line-height: 2em;
    box-sizing: border-box;
    border-radius: 4px;
    border: 1px solid rgba(2, 21, 49, 0.95);
    background-color: rgba(255, 255, 255, 0.05);
  }

  .day.valid {
    cursor: pointer;
    background-color: rgba(255, 255, 255, 0.2);
  }
</style>
```

### 3. Apply the _.valid_ class to days that are in the selected month.

Hint: the `isInReqMonth` property returns true if the day is in the selected month
