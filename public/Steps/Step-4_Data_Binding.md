## Step 4: Data Binding

In the previous step we added some state (data) to our components. In this section we will go a little further with data-binding.

In a Vue.js, data is initialized using a function, e.g.:

```javascript
data: function() {
	return {
		selectedDate: null
	};
}
```

The reason a function is used to initialize the data, is to ensure that every instance of a component gets it's own state, and does not share it's data with other components, which could cause unwanted and unpredictable side effects.

## Binding input controls to component data

In Vue.js, it is usually not neccesary to create event handlers and do manual updates for input fields. Vue.js has the _v-model_ attribute for that:

```html
<input v-model="message" placeholder="edit me" />
<p>Message is: {{ message }}</p>
```

<i class="far fa-hand-point-down fa-2x"></i>

## Todo(s)

### 1. Show appointments when selecting date

- Use the `getAppointments` function in helpers.js to initialise the appointment data in the _Appointments_ component.

- Show the appointments for the selected date

- Important appointments are highlighted in red

### 2. Make the description and importance of appointments editable

- You might not want to make the time editable just yet.
