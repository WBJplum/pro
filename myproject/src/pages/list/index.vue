<template>
<div>
    <p> </p>
    <i-grid i-class="no-border">
    <i-grid-item >
    <i-grid-label>口红专栏</i-grid-label>
    </i-grid-item>
    </i-grid>
      <view v-for="item in lipstick" :key='item' class="top-padding">
     <i-card :title="item.name" :thumb="item.photo">
       <view slot="content">介绍：{{item.intro}}</view>
       <view slot="content">色号推荐：{{item.type}}</view>
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
