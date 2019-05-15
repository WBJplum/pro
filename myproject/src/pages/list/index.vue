<template>
<div>
    <i-panel title="分类推荐">
      <view v-for="item in lipstick" :key='item' class="top-padding">
     <i-card :title="item.name" :extra="item.png" :thumb="item.photo">
       <view slot="content">{{item.intro}}</view>
       <view slot="content">{{item.type}}</view>
       </i-card>
    </view>
    </i-panel>
    </div>
</template>

<script>


export default {

  data () {
    return {
      lipstick: []
    }
  },

  onLoad (option){
    console.log(option.type)
    //this.recommand = require('/data/' + option.type + '.json')
  },

   created () {
    const db = wx.cloud.database({ env: 'store-2cfefc'})
    db.collection('lipstick').get().then(
      res => {
        console.log(res.data)
        this.lipstick = res.data
      }
    )
  }
}
</script>

<style scoped>
div >>> .split {
  margin-bottom: 10pt;
}
</style>
