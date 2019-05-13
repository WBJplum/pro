<template>
<div @click="clickHandle">
    <i-notice-bar icon="systemprompt" loop :speed='1500' :color="'black'">
    {{notice}}各种美妆品牌详解！！
    </i-notice-bar>
        <i-grid i-class="no-border">
    <i-grid-item >
    <i-grid-icon>
    <image src="/static/images/lipstick.png" />
    </i-grid-icon>
    <i-grid-label>Lipstick</i-grid-label>
    </i-grid-item>
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
      recommand: []
    }
  },

  onLoad (option){
    console.log(option.type)
    //this.recommand = require('/data/' + option.type + '.json')
  },

  created () {
  }
}
</script>

<style scoped>
div >>> .split {
  margin-bottom: 10pt;
}
</style>
