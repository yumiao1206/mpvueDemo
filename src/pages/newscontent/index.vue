<template>
  <div>
    <h2>{{list.title}}</h2>
    <div v-html="list.content">
    </div>
    <!--<wxParse :content="list.content" />-->
  </div>
</template>

<script>
// import wxParse from 'mpvue-wxparse';

 // 注意：创建页面的时候必须暴露，否则会卡死
export default {
  // components: {
  //   wxParse
  // },
  data () {
    return {
      list: [],
    }
  },
  methods: {
    requestData(aid){
      var that = this;
      var api = 'http://www.phonegap100.com/appapi.php';
      wx.request({
        url: api,
        data: {
          a: 'getPortalArticle',
          aid: aid,
        },
        header: {
          'content-type': 'application/json'
        },
        success: function(res) {
          console.log(res.data)
          that.list = res.data.result[0];
        }
      })
    }
  },
  onLoad(options) {
    console.log(options)
    var aid = options.aid;
    this.requestData(aid);
  }
}
</script>

<style scoped>
/*@import url("~mpvue-wxparse/src/wxParse.css");*/

.content {
  line-height: 2;
}
.content img{
  max-width: 90%;
  margin: 0 auto;
}

</style>
