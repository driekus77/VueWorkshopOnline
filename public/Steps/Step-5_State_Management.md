## Step 5: State Management

The Vuex developers looked a lot at the React Flux pattern (Facebook): https://www.freecodecamp.org/news/an-introduction-to-the-flux-architectural-pattern-674ea74775c9/ when developing there tool.

### What is it?

Vuex is a state management pattern + library for Vue.js applications. It serves as a centralized store for all the components in an application, with rules ensuring that the state can only be mutated in a predictable fashion. From: https://vuex.vuejs.org/

### When to use it?

If you have lots of components that need to communicate with eachother or you need a central place to store youre components state than state manager like Vuex can com in handy!

### How to use it?

There are different discussions on this topic on the internet. The main advise is to use normalized state, so no deeply nested json inside your state.
For a interessting article about Normalized Vuex state use see: https://markus.oberlehner.net/blog/make-your-vuex-state-flat-state-normalization-with-vuex/

The best way to think about a Vuex state is handle it like a (relational) database. Normalizing your state is a little bit more work but pays of in less complexity and easy synchronisation with your (relational?) backend.

### Install Vuex in your app

You can install Vuex in your Vue js app as a "normal" lib/plugin in your main/index .js file where Vue is instanciated:

```javascript
// file: main.js
import Vue from "vue";

import App from "./App.vue";
import store from "./store";

Vue.config.productionTip = false;

new Vue({
  render: h => h(App),
  store: store // <-- Don't forget to register your store!
}).$mount("#app");
```

### Setup an example state

For Vuex, just as with Vue local state, you can not bind on complex objects with deeply nested structure(s). For the rest can you add everything you want.

```javascript
const state = {
  byId: {},
  allIds: []
};
```

### Make your state available (readable) through getters

```javascript
const getters = {
  // Return a single appointment with the given id.
  // From flat (normalized) to nested
  find: (state, _, __, rootGetters) => id => {
    // Swap ID referenes with the resolved author objects.
    return resolveRelations(state.byId[id], [], rootGetters);
  },
  // Return a list of appointments in the order of `allIds`.
  list: (state, getters) => {
    return state.allIds.map(id => getters.find(id));
  }
};
```

### Make your state mutable (writeable) through mutations

Advice / Tip: Always use an action in front of a mutation!
Note: Mutations are synchronious!

```javascript
const mutations = {
  ADD: (state, item) => {
    Vue.set(state.byId, item.id, item);
    if (state.allIds.includes(item.id)) return;
    state.allIds.push(item.id);
  },
  MODIFY: (state, item) => {
    Vue.set(state.byId, item.id, item);
  },
  REMOVE: (state, item) => {
    if (!state.allIds.includes(item.id)) return;
    Vue.delete(state.byId, item.id);
    var idx = state.allIds.indexOf(item.id);
    state.allIds.splice(idx, 1);
  }
};
```

### Add actions to your state through actions

Note: Actions are asynchronious!

```javascript
const actions = {
  async load({ commit }) {
    const appointments = await appointmentService.list();
    appointments.forEach(item => {
      commit("ADD", normalizeRelations(item, []));
    });
  },

  async save({ commit, state }, item) {
    if (state.allIds.includes(item.id)) {
      commit("MODIFY", normalizeRelations(item, []));
    } else {
      commit("ADD", normalizeRelations(item, []));
    }
  }
};
```

### Organize your store using modules

Vuex modules are nice to keep a clean overview of your state / store.

```javascript
// file: store/index.js
// note: This example uses normalized state
import Vue from "vue";
import Vuex from "vuex";

import appointment from "./modules/appointment";

Vue.use(Vuex);

export default new Vuex.Store({
  modules: {
    appointment
  },
  strict: true
});
```

Note: in above example we used strict mode which is helpfull during development in throwing errors when the state is per acident mutated.

And in your module file don't forget to register all your parts:

```javascript
...
export default {
  namespaced: true,
  actions,
  getters,
  mutations,
  state
};
```

### Use your store / state from inside your Vue app

There are different ways to access state from within your compoments. Beneath an overview:

Access state through this.\$store.state....

```javascript
	computed: {
		fullName:
			get() {
				this.$store.state.firstName + " " + this.$store.state.lastName;
			}
	}
```

Access state through this.\$store.getters....

```javascript
	computed: {
		fullName:
			get() {
				this.$store.getters.getFirstName() + " " + this.$store.getters.getLastName();
			}
	}
```

Mutate state through mutation commit...

```javascript
	methods: {
		saveFirstName(firstName) {
			this.$store.commit("MODIFY", firstName);
		}
	}
```

Run action by dispatch...

```javascript
	methods: {
		saveLastName(lastName) {
			this.$store.dispatch("savePerson", {lastName: lastName});
		}
	}
```

### mapState, mapGetters, mapMutations, mapActions, ... Vuex helper methods

If you don't like typing computed properties for each field your form has there are plenty of helper methods available!

<i class="far fa-hand-point-down fa-2x"></i>

## TODO(S)

1. Add vuex to your app
2. Move appointments to your store
3. Move Selected day to store
4. Check app is still working!
5. Make MonthView use appointments from store its state and color important appointments in e.g. red.
