## Component(s)

A Vue app is build out of one or multiple components. A component can contain 3 part:

- (X)HTML as markup template
- Javascript or Typescript as scripting language
- CSS/SCSS/SASS/LESS for styling

These three parts can be provided in 2 ways:

#### _Javascript/CSS files (.js/.css) as base:_

```javascript
// src/components/App.js
export default {
  name: "App",
  template: `
    <div class="container mx-auto p-4">
      <h1>Hello World</h1>
    </div>
  `
};
```

When to use: Above setup is easy to use in existing apps or when you don't want to use webpack!

#### _Everything in a Single File Component (SFC):_

file: Mycomponent.vue:

```html
<template>
  <div class="#app">
    <componenta />
    <componentb />
    ...
  </div>
</template>

<script>
  import ComponentA from "./components/ComponentA";
  import ComponentB from "./components/ComponentB";
  ...

  export default {
    name: "MyComponent",
    components: {
      ComponentA,
      ComponentB,
      ...
    }
  };
</script>

<style>
  #app {
    background-color: var(--bloemertlight-color);
  }
</style>
```

Above SFC is the most used and the one we use together with HTML, Javascript and CSS, in the rest of this workshop.

## Properties

You can use properties to pass data from Parent to Child components.

Usage in Parent:

```html
<template>
  ...
  <my-child myprop="mydata" />
  ...
</template>
...
```

Definition in Child:

```html
...
<script>
  export default {
    name: "my-child",
    props: ["myprop"]
  };
</script>
...
```

Inside the child's javascript a property can be accessed via this.myprop or in the HTML using double mustage syntax:

```html
<template>
  <div>{{myprop}}</div>
</template>
```

<i class="far fa-hand-point-down fa-2x"></i>

## Todo(s):

### Create 2 components

- Create a AgendaApp component as replacement for the Steps component.
  Hints: Create a new file named "AgendaApp.vue" and replace inside App.vue the Steps references with your new Component name.
  Note: If you don't want to work with the SPA setup in App.vue you can also replace App.vue its implementation. Its up to you!
- Create a MonthView component and add it too your AgendaApp.

### Create 2 Properties

- Add properties Month and Year too the MontView component and make sure that they are shown.
