## Step 4: Data Binding

In the previous step we added some state (data) to our components. In this section we will go a little further with data-binding.

In a Vue.js, data is initialized using a function, e.g.:

```javascript
  data: function() {
    return {
      selectedDate: null
    };
	},
```

The reason a function is used to initialize the data, is to ensure that every instance of a component gets it's own state, and does not share it's data with other components, which could cause unwanted and unpredictable side effects.

    	Afspraken view leest afspraken.json in (wordt aangeleverd) en toont de afspraken voor de geselecteerde dag.
    	Structuur afspraken:
    		- uuid
    		- description
    		- dateAndTime
    		- label (important / normal)
    	Afpsraken met label important krijgen rode balk o.i.d.
