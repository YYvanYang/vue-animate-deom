<template>
<div id="list-complete-demo" class="demo">
  <button v-on:click="shuffle">Shuffle</button>
  <button v-on:click="add">Add</button>
  <button v-on:click="remove">Remove</button>
  <div>动画对比</div>
  <div>demo1:enter-to,leave-to</div>
  <transition-group name="list-complete" tag="p" enter-to-class="animated bounceInRight" 
  leave-to-class="animated zoomOutLeft">
    <span
      v-for="item in items"
      v-bind:key="item"
      class="list-complete-item"
    >
      {{ item }}
    </span>
  </transition-group>

  <br>
  <div>demo2:enter-active,leave-active</div>

  <transition-group name="list-complete" tag="p" enter-active-class="animated bounceInRight" 
  leave-active-class="animated zoomOutLeft">
    <span
      v-for="item in items"
      v-bind:key="item"
      class="list-complete-item"
    >
      {{ item }}
    </span>
  </transition-group>

  <div>demo3:enter-class</div>

  <transition-group name="list-complete" tag="p" enter-class="animated bounceInRight" 
  leave-class="animated zoomOutLeft">
    <span
      v-for="item in items"
      v-bind:key="item"
      class="list-complete-item"
    >
      {{ item }}
    </span>
  </transition-group>
</div>
</template>

<script>
import _ from 'lodash'
import Velocity from 'velocity-animate'

export default {
  name: 'HelloWorld',
  data () {
    return {
     items: [1,2,3,4,5,6,7,8,9],
    nextNum: 10
    }
  },
   methods: {
    randomIndex: function () {
      return Math.floor(Math.random() * this.items.length)
    },
    add: function () {
      this.items.splice(this.items.length, 0, this.nextNum++)
    },
    remove: function () {
      this.items.splice(0, 1)
    },
    shuffle: function () {
      this.items = _.shuffle(this.items)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.list-complete-item {
  /* transition: all 1s; */
  display: inline-block;
  margin-right: 10px;
}

/* <transition-group> 组件还有一个特殊之处。
不仅可以进入和离开动画，还可以改变定位。
要使用这个新功能只需了解新增的 v-move 特性，
它会在元素的改变定位的过程中应用。
像之前的类名一样，可以通过 name 属性来自定义前缀，
也可以通过 move-class 属性手动设置。 */
.list-complete-move {
  transition: all 1s;
}

.list-complete-leave-active {
  position: absolute;
}


</style>
