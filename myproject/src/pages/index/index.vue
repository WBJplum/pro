<template>
  <div @click="clickHandle">
    <i-notice-bar icon="systemprompt" loop :speed='1500' :color="'pink'">
    {{notice}}店铺推荐
    </i-notice-bar>
    <i-grid i-class="no-border">
    <i-grid-item >
    <i-grid-icon>
    <image src="/static/images/nail polish.png" />
    </i-grid-icon>
    <i-grid-label>美甲</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
    <i-grid-icon>
    <image src="/static/images/make up.png" />
    </i-grid-icon>
    <i-grid-label>美妆</i-grid-label>
    </i-grid-item>
      </i-grid>
    <i-grid i-class="no-border">
    <i-grid-item >
    <i-grid-icon>
    <image src="/static/images/skin.png" />
    </i-grid-icon>
    <i-grid-label>搭配</i-grid-label>
    </i-grid-item>
    <i-grid-item >
    <i-grid-icon>
    <image src="/static/images/Hairdresser.png" />
    </i-grid-icon>
    <i-grid-label>洗发</i-grid-label>
    </i-grid-item>
    </i-grid>
    <i-grid i-class="no-border">
      <i-grid-item i-class="no-border">
    <i-grid-icon>
    </i-grid-icon>
    <i-grid-label></i-grid-label>
    </i-grid-item>
    </i-grid>
    <p>热推</p>
    <view v-for="item in beauty" :key='item' class="top-padding">
     <i-card :title="item.name" :extra="item.id" :thumb="item.photo">
       <view slot="content">位置：{{item.place}}</view>
       <view slot="content">店铺介绍：{{item.intro}}</view>
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
