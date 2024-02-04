# vue-roll-number

Number changing animation Vue.js component.

From v2.0.0, it works for Vue 3.

## Demo

[Demo](https://sandbox.serendip.ws/vue-roll-number.html)


## Install

### Browser

```html
<script src="vue.global.prod.js"></script>
<script src="vue-roll-number.umd.js"></script>
```


### npm

```
npm install --save @inotom/vue-roll-number
```


## Usage

### Browser

```html
<div id="app">
  <roll-number number-value="1,920" />
</div>

<script src="vue.global.prod.js"></script>
<script src="vue-roll-number.umd.js"></script>
<script>
const { createApp } = Vue;
const { RollNumber } = SwsVueRollNumber;

createApp({
  components: {
    RollNumber,
  },
}).mount('#app');
</script>
```


### SFC (TypeScript)

```vue
<template>
  <roll-number number-value="1,920" />
</template>

<script setup lang="ts">
import { RollNumber } from '@inotom/vue-roll-number';
</script>
```

## Props

| name              | type     | defaults      | description                 |
|-------------------|----------|---------------|-----------------------------|
| `number-value`    | `String` | ``            | Numbar value (required)     |
| `:anim-duration`  | `Number` | `3000`        | Animation duration time(ms) |
| `:anim-interval`  | `Number` | `10`          | Animation interval time(ms) |
| `block-name`      | `String` | `roll-number` | Custom class name           |


## License

MIT


## Author

inotom
