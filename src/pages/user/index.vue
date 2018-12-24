<template>
  <div>
    {{msg}}
    <br />
    <button @click="run()">触发事件</button>
    <br />
    <ul>
      <li v-for="item in list" :key=item>
        {{item}}
      </li>
    </ul>
    <img src="../../../static/images/home2.png" alt="">
  </div>
</template>

<script>

 // 注意：创建页面的时候必须暴露，否则会卡死
export default {
  data () {
    return {
      msg: '我是一个用户组件',
      list: []
    }
  },
  methods: {
    run () {
      console.log('执行方法')
    }
  },
  // 生命周期函数可以用vue的，也可以用小程序的
  created () {
    for (let i = 0; i < 10; i++) {
      this.list.push(i);
    }
  }
}
</script>

<style scoped>

</style>
