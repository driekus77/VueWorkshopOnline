## Declarative Rendering

From: https://vuejs.org/v2/guide/#Declarative-Rendering
At the core of Vue.js is a system that enables us to declaratively render data to the DOM using straightforward template syntax:

```html
<div id="myid">
  {{ message }}
</div>
<script>
  var app = new Vue({
    el: "#myid",
    data() {
      return {
        message: "Hello Vue!"
      };
    }
  });
</script>
```

## Conditionals & Loop directives

**"v-if"** directive example:

```html
<template>
  <div id="app-3">
    <span v-if="seen">Now you see me</span>
  </div>
</template>
<script>
  var app3 = new Vue({
    el: "#app-3",
    data: {
      seen: true
    }
  });
</script>
```

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

### Use provided helper methods to generate a view of days per month.

e.g.:

```html
<script>
  import { getFullMonthName, getCalendarMonth } from "../helpers";
  ...
</script>
```
