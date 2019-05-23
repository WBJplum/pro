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
      <p> </p>
    <i-grid i-class="no-border">
    <i-grid-item >
    <i-grid-label>眼影专栏</i-grid-label>
    </i-grid-item>
    </i-grid>
      <view v-for="item in eyeshadow" :key='item' class="top-padding">
     <i-card :title="item.name" :extra="item.from" :thumb="item.photo">
       <view slot="content">介绍：{{item.intro}}</view>
       <view slot="content">类型推荐：{{item.type}}</view>
       </i-card>
    </view>
      <p> </p>
    <i-grid i-class="no-border">
    <i-grid-item >
    <i-grid-label>香水专栏</i-grid-label>
    </i-grid-item>
    </i-grid>
      <view v-for="item in perfume" :key='item' class="top-padding">
     <i-card :title="item.name" :extra="item.from" :thumb="item.photo">
       <view slot="content">创造人：{{item.inventor}}</view>
       <view slot="content">类型推荐：{{item.type}}</view>
       </i-card>
    </view>
    </div>
</template>

<script>


export default {

  data () {
    return {
      lipstick: [],
      eyeshadow: [],
      perfume: []
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
        db.collection('eyeshadow').get().then(
      res => {
        console.log(res.data)
        this.eyeshadow = res.data
      }
    )
      db.collection('perfume').get().then(
      res => {
        console.log(res.data)
        this.perfume = res.data
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
