<template>
<div>
  <view v-for="item in jump" :key='item' class="top-padding">
     <i-card :title="item.name" :thumb="item.photo">
       <view slot="content">实体店位置：{{item.adress}}</view>
       <view slot="content">色号：{{item.type}}</view>
       <view slot="content">连接：{{item.http}}</view>
       </i-card>
  </view>
</div>
</template>

<script>

export default {
  data () {
    return {
    jump:[],
     list:[]
    }
  },

   methods: { 
     requestData(a){
       var that=this;
       var apl='http://www.phonegap100.com/appai.php?a=getPortalArticle&a'+a;
    wx.request({
      url:a,
      header: {
        'content-type': 'application/json'
      },
      success: function(res) {
        console.log(res.data)
      }
    })
     }     
  },
  onload: function(options){
    var a=options.a;
    this.requestData(a);
  },

  created () {
    const db = wx.cloud.database({ env: 'store-2cfefc'})
    db.collection('jump').get().then(
      res => {
        console.log(res.data)
        this.jump = res.data
      }
    )
  }
 }
</script>
