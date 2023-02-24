<template>
  <div class="app-container">
    <h1>App 根组件</h1>
    <hr />

    <button @click="comName = 'Left'">展示Left</button>
    <button @click="comName = 'Right'">展示Right</button>
    <div class="box">
      <!-- 渲染 Left 组件和 Right 组件 -->
      <!-- <Left></Left> -->
      <!-- 1.component标签是vue内置的，作用：组件的占位符 -->
      <!-- 2.is属性的值，表示要渲染的组件的名字 -->
      <keep-alive include="MyLeft,MyRight">
        <!-- keepalive可以把内部的组件进行缓存，而不是销毁组件 -->
        <component :is="comName"></component>
      </keep-alive>
      <!-- <Right></Right> -->
    </div>
  </div>
</template>

<script>
import Left from '@/components/Left.vue';
import Right from '@/components/Right.vue';
export default {
  data() {
    return {
      //comName表示要展示的组件的名字
      comName: 'Left'
    }
  },
  components: {
    //如果在“声明组件”的时候，没有为组件指定name名称，则组件的名称默认就是注册时候的名称
    Left,
    Right
  }
}
</script>

<style lang="less">
.app-container {
  padding: 1px 20px 20px;
  background-color: #efefef;
}
.box {
  display: flex;
}
</style>
