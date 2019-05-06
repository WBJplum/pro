<template>
  <div>
    <i-panel title="分类推荐">
      <view v-for="item in beauty" :key='item' class="top-padding">
     <i-card :title="item.name" :extra="item.id" :thumb="item.photo">
       <view slot="content">{{item.place}}</view>
       <view slot="content">{{item.intro}}</view>
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
