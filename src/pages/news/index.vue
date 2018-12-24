<template>
  <div>
    <ul class="list">
      <li v-for="(item, key) in list" :key="key" @click="goContent(item.aid)">
        {{item.title}}
      </li>
    </ul>
  </div>
</template>

<script>

 // 注意：创建页面的时候必须暴露，否则会卡死
export default {
  data () {
    return {
      list: [],
    }
  },
  methods: {
    requestData(){
      var that = this;
      var api = 'http://www.phonegap100.com/appapi.php';
      wx.request({
        url: api,
        data: {
          a: 'getPortalList',
          catid: '20',
          page: '1'
        },
        header: {
          'content-type': 'application/json'
        },
        success: function(res) {
          // console.log(res.data)
          that.list = res.data.result;
        }
      })
    },
    goContent(aid){
      const url = '../newscontent/main?aid=' + aid;
      wx.navigateTo({url});
    }
  },
  created() {
    this.requestData();
  }
}
</script>

<style scoped>
.list {
  padding: 5px;
}
.list li{
  height: 40px;
  line-height: 40px;
  text-decoration: underline;
  overflow: hidden;
}
</style>
