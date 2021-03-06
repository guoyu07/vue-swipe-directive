
## vue-swipe-directive

### 使用

```vue
<template>
  <div v-swipe:vertical="swipeConfig"></div>
</template>

<script>
  import { swipeDirective } from '../../mixins/event/swipe.js'

  export default {
    mounted () {
      this.swipeConfig = {
        start: (info, lock, propagation) => console.log(info),
        move:  (info, lock, propagation) => console.log(info),
        end:   (info, lock, propagation) => console.log(info)
      }
    },

    directives: {
      // 指令名字可自定义
      swipe: swipeDirective
    }
  }
</script>
```

#### swipeDirective的参数

```vue
<div v-swipe:direction.lock="swipeConfig"></div>

direction: any, horizonal, vertical, right, left, up, down
modifiers: lock
// 当识别到direction的时候就会lock, 会和滚动互斥, 事件不会往上冒泡

swipeConfig: {
  start: Function,
  move:  Function,
  end:   Function
}
```

### 回调参数

```js
info = {
  scrEvt: Event,
  offset: Number,
  startY: Number,
  startX: Number,
  movingX: Number,
  movingY: Number,
  element: HTMLElement,
  directionTwo: String,  // horizonal, vertical
  directionFour: String, // right, left, up, down
};

lock        = Function(Boolean); // lock(true/false)        是否执行preventDefault
propagation = Function(Boolean); // propagation(true/false) 是否执行stopPropagation
```

## License

MIT 一起来扣细节~