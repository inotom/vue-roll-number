# vue-roll-number

Number changing animation Vue.js component.


## Demo

[Demo](http://sandbox.serendip.ws/vue-roll-number.html)


## Install

### Browser

```html
<script src="vue.js"></script>
<script src="vue-roll-number.min.js"></script>
```


### npm

```
npm install --D @inotom/vue-roll-number
```


## Usage

### Browser

```html
<div id="app">
  <roll-number number-value="1,920" />
</div>

<script src="vue.js"></script>
<script src="vue-roll-number.min.js"></script>
<script>
Vue.use(RollNumber);
new Vue({
  el: '#app'
});
</script>
```


### SFC

```vue
<template>
  <roll-number number-value="1,920" />
</template>

<script>
import RollNumber from '@inotom/vue-roll-number';

export default {
  components: {
    RollNumber,
  }
}
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
