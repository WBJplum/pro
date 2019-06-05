<template>
<div>
  <view v-for="item in meizhuang" :key='item' class="top-padding">
     <i-card :title="item.name">
       <view slot="content">介绍：{{item.intro}}</view>
       </i-card>
  </view>
</div>
</template>

<script>

export default {
  data () {
    return {
    meizhuang:[],
     list:[]
    }
  },

   methods: { 
     requestData(b){
       var that=this;
       var apl='http://www.phonegap100.com/appai.php?a=getPortalArticle&a'+a;
    wx.request({
      url:b,
      header: {
        'content-type': 'application/json'
      },
      success: function(res) {
        console.log(res.data)
      }
    })
     }     
  },
  onload: function(b){
    var b=options.b;
    this.requestData(b);
  },

  created () {
    const db = wx.cloud.database({ env: 'store-2cfefc'})
    db.collection('meizhuang').get().then(
      res => {
        console.log(res.data)
        this.meizhuang = res.data
      }
    )
  }
 }
</script>