<template>
  <div @click="clickHandle">
    <i-notice-bar icon="systemprompt" loop>
    {{notice}}巴拉巴拉
    </i-notice-bar>
    <i-grid i-class="no-border">
    <i-grid-item i-class="no-border">
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
    <i-grid-item i-class="no-border">
    <i-grid-icon>
    <image src="/static/images/skin.png" />
    </i-grid-icon>
    <i-grid-label>搭配</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
    <i-grid-icon>
    <image src="/static/images/Hairdresser.png" />
    </i-grid-icon>
    <i-grid-label>洗发</i-grid-label>
    </i-grid-item>
    </i-grid>
     <Row style="background:#eee;padding:20px">
        <i-col span="11">
            <Card :bordered="false">
                <p slot="title">无边框卡片</p>
                <p>卡片内容</p>
                <p>卡片内容</p>
                <p>卡片内容</p>
            </Card>
        </i-col>
        <i-col span="11" offset="2">
            <Card shadow>
                <p slot="title">使用阴影效果的卡片</p>
                <p>卡片内容</p>
                <p>卡片内容</p>
                <p>卡片内容</p>
            </Card>
        </i-col>
    </Row>



    
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
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
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    }
  },

  created () {
    const db = wx.cloud.database({ env: ''})
    db.collection('shop').get().then(
      res => {
        this.shops = res.data
      }
    )
    wx.cloud.callFuction({ name: 'W1324-66'}).then(
      res =>{
        console.log(res)
      }
    )
  }
}
</script>

<style scoped>
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}

.usermotto {
  margin-top: 150px;
}

.form-control {
  display: block;
  padding: 0 12px;
  margin-bottom: 5px;
  border: 1px solid #ccc;
}
.all{
  width:7.5rem;
  height:1rem;
  background-color:blue;
}
.all:after{
  display:block;
  content:'';
  clear:both;
}
.left{
  float:left;
  width:3rem;
  height:1rem;
  background-color:red;
}

.right{
  float:left;
  width:4.5rem;
  height:1rem;
  background-color:green;
}
</style>
