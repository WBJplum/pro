<template>
<div>
  <view v-for="item in beauty" :key='item' class="top-padding">
     <i-card :title="item.name" :extra="item.id" :thumb="item.photo">
       <view slot="content">位置：{{item.place}}</view>
       <view slot="content">店铺介绍：{{item.intro}}</view>
       </i-card>
  </view>
</div>
</template>

<script>

export default {
  data () {
    return {
    beauty:[],
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
    db.collection('beauty').get().then(
      res => {
        console.log(res.data)
        this.beauty = res.data
      }
    )
  }
 }
</script>
