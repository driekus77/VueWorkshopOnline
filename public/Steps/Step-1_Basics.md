## Step 1: Basics

A Vue app is build up out of one or multiple components. A component contains 3 part:

- HTML inside the template
- Javascript as script
- CSS/SCSS/SASS/LESS inside style

These three parts can be provided in 2 ways:

- Javascript/CSS files (.js/.css) as base:

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

- Everything in a Single File Component (SFC):

```html
<template>
  <div class="#app">...</div>
</template>

<script>
  export default {
    name: "MyVueComponent",
    components: ["SubComponentA", "SubComponentB", "SubComponentC"]
  };
</script>

<style>
  #app {
    color: blue;
  }
</style>
```

Above SFC is the most used and the one we use in the rest of this workshop.

### Workshop assignment:

    	Componenten
    		App heeft al title component
    		Deelnemer moet MonthView component aanmaken en toevoegen aan de app
    	Properties
    		Deelnemer voegt maand en jaar properties toe aan monthview component, component toont maand en jaar
