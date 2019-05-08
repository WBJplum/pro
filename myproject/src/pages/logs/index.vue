<template>
  <div @click="clickHandle">
    <view v-for="item in beauty" :key='item' class="top-padding">
     <i-card :title="item.name" :extra="item.id" :thumb="item.photo">
       <view slot="content">{{item.place}}</view>
       <view slot="content">{{item.intro}}</view>
       </i-card>
    </view>
    </div>
</template>

<script>

import card from '@/components/card'

export default {
  data () {
    return {
      beauty:[],
      motto: 'Hello miniprograme',
      userInfo: {
        nickName: 'mpvue',
        avatarUrl: 'http://mpvue.com/assets/logo.png'
      }
    }
  },

  components: {
    card
  },


  methods: {      
    goList (url) {
      mpvue.navigateTo({ url })
    },
    goType (type) {
      let url = '../list/main?type=' + type
      mpvue.navigateTo({ url })
    }
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

<style scoped>
  div >>>.no-border{
border-whdth: 0pt;
  }
</style>

