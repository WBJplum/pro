<template>
  <div>
    <view class="userinfo">
    <view class="userinfo-avatar">
    <open-data type="userAvatarUrl"></open-data>
    </view>
    <open-data type="userNickName"></open-data>
    </view>
    <i-panel title="我是精致的猪猪女孩，我要推荐！">
      <i-input :value="type" @change="changeType($event)" title="推荐类型" placeholder="请输入推荐类型" maxlength="30" />
      <i-input :value="name" @change="changeName($event)" title="店铺名称" autofocus placeholder="请输入店名" maxlength="20" />
      <i-input :value="address" @change="changeAddress($event)" title="详细地址" placeholder="请输入详细地址" maxlength="30" />
      <i-input :value="reason" @change="changeReason($event)" title="推荐理由" placeholder="请输入推荐理由" maxlength="50" />
    </i-panel>
    <i-button @click="handleClick" type="warning" size="default">我要推荐</i-button>
    <view class="tips">装扮专用小程序，如果你有美甲、美妆、搭配、洗发方面的推荐，请分享！！</view>
  </div>
</template>

<script>

export default {

  data () {
    return {
      type:"",
      name:"",
      address:"",
      reason:""
    }
  },

  methods: {
    changeType (event) {
      this.type = event.mp.detail.detail.value
    },
    changeName (event) {
      this.name = event.mp.detail.detail.value
    },
    changeReason (event) {
      this.reason = event.mp.detail.detail.value
    },
    changeAddress (event) {
      this.address = event.mp.detail.detail.value
    },
    handleClick () {
      if (this.type && this.name && this.reason && this.address) {
        wx.showToast({
          title: '推荐了' +this.type+ '的' + this.name + '店铺',
          icon: 'success',
          duration: 2000
        })
        // TODO:将推荐数据提交到云数据库
      } else {
        wx.showToast({
          title: '信息不完整',
          icon: 'none',
          duration: 2000
        })
      }
    }
  },

  created () {
  }
}
</script>

<style scoped>
.userinfo {
  position: relative;
  width: 750rpx;
  height: 320rpx;
  color: #666;
  display: flex;
  flex-direction: column;
  align-items: center;
}
 
.userinfo-avatar {
  overflow:hidden;
  display: block;
  width: 160rpx;
  height: 160rpx;
  margin: 20rpx;
  margin-top: 50rpx;
  border-radius: 50%;
  border: 2px solid #fff;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
}

.tips {
  padding: 20pt;
  font-size: 10pt;
  color:darkorange;
}
</style>

