# Vue JS

## Creating A Vue App

```javascript
const app = Vue.createApp({
  // Options
});
app.mount("#app");
```

## Template Syntax

- **Interpolation**: `{{ message }}`
- **Directives**: v-bind:href="url", v-if="seen", v-for="item in items"
- **Event Handling**: v-on:click="doSomething"

## Reactivity

- `ref()` for primitive values.

```javascript
// ref()
import { ref } from "vue";

const count = ref(0);
console.log(count.value); // 0
```

- `reactive()` for objects and arrays.

```javascript
// reactive()
import { reactive } from "vue";

const state = reactive({
  name: "Vue",
  version: 3,
});
console.log(state.name); // Vue
```

## Computed Properties

- `computed()`: a function to transform or calculate a ref object.

```javascript
// computed()
import { ref, computed } from "vue";

const count = ref(2);
const double = computed(() => count.value * 2);

console.log(double.value); // 4
```

## Watchers

- `watch()`: trigger a callback whenever a piece of reactive state changes.

```javascript
// watch
import { ref, watch } from "vue";

const name = ref("Vue");

watch(name, (newValue, oldValue) => {
  console.log(`Name changed from ${oldValue} to ${newValue}`);
});
```

## Lifecycle Hooks

|      Hooks      | Description                                                                                                    |
| :-------------: | :------------------------------------------------------------------------------------------------------------- |
|  `onMounted()`  | Registers a callback to be called after the component has been mounted.                                        |
| `onUnmounted()` | Registers a callback to be called after the component has been unmounted.                                      |
|  `onUpdated()`  | Registers a callback to be called after the component has updated its DOM tree due to a reactive state change. |

## Props and Emits

- props: custom attributes you can register on a component.

```javascript
// declaration
defineProps({
  title: String,
  likes: Number,
});
```

- emits: emits events from script setup.

```javascript
const emit = defineEmits(["enlarge-text"]);

emit("enlarge-text");
```

## Using Plugins

- Plugins are self-contained code that usually add app-level functionality to Vue. This is how we install a plugin:

```javascript
const app = createApp({});

app.use(myPlugin, {
  /* optional options */
});
```
