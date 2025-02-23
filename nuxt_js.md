# Nuxt JS

## Project Structure

```arduino
my-nuxt-app/
├── assets/
├── components/
├── composables/
├── layouts/
├── middleware/
├── pages/
├── plugins/
├── public/
├── server/
├── app.vue
├── nuxt.config.ts
```

## Pages & Routing

- **Automatic Routing**: Files in `pages/` directory automatically create routes.

```vue
<!-- pages/index.vue -->
<template>
  <div>Home Page</div>
</template>
```

- **Dynamic Routing**: Use square brackets or dynamic parameters.

```vue
<!-- pages/users/[id].vue -->
<template>
  <div>User ID: {{ id }}</div>
</template>

<script setup lang="ts">
import { useRoute } from "vue-router";
const route = useRoute();
const id = route.params.id;
</script>
```

## Layouts

- **Default Layout**: Create deault layout that wraps around page components.

```vue
<!-- layouts/default.vue -->
<template>
  <div>
    <NavBar />
    <NuxtPage />
  </div>
</template>
```

## Composition API Basics

- Reactive State:

```vue
<template>
  <div>{{ count }}</div>
</template>

<script setup lang="ts">
const count = ref(0);
</script>
```

- Computed Properties:

```vue
<template>
  <div>{{ double }}</div>
</template>

<script setup lang="ts">
const count = ref(0);
const double = computed(() => count.value * 2);
</script>
```

- Lifecycle Hooks:

```vue
<script setup lang="ts">
onMounted(() => {
  console.log("Component mounted");
});
</script>
```
