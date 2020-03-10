## Component(s)

A Vue app is build out of one or multiple components. A component can contain 3 parts:

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
  <my-child myprop="Vue.js workshop" />
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

Inside the child's javascript a property can be accessed via this.myprop or in the HTML using "Mustache" syntax:

```html
<template>
  <div>{{myprop}}</div>
</template>
```

## Declarative Rendering

In above example, the {{myprop}} declaration results in the value of the property _myprop_ being rendered inside the div. The result of this code will be:

```html
<div>Vue.js workshop</div>
```

This technology is called "Declarative Rendering" and is the core concept in Vue.js.

More details about declarative rendering can be found at: (<https://vuejs.org/v2/guide/#Declarative-Rendering>)

<i class="far fa-hand-point-down fa-2x"></i>

## Todo(s):

### 1. Create 2 components

1. Create an Agenda component as replacement for the HelloWorld component (you can find this component in the /src/components folder).

Hints:

- Create a new file named "Agenda.vue" in the src/components folder
- You might like to copy the contents of the HelloWorld component to get started
- Import your component in App.vue.

2. Create a MonthView component and use it in your Agenda component.

### 2. Create 2 Properties

- Add properties _month_ and _year_ to the MonthView component, set them from the Agenda component and make sure that they are shown.
