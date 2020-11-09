<template>
  <view class="content">
    <view class="container">
      <view class="pageBox" style="padding: 10% 10%">
        <view
          style="
            height: 1px;
            width: 100%;
            margin: 20px auto;
            background: #e8e8e8;
          "
        ></view>
        <view style="margin: 40px 0">
          <text style="color: #000000; font-weight: bold"
            >申请获取以下权限</text
          >
          <text style="color: #c1b6b4">获得你的公开信息（昵称，头像等）</text>
        </view>
        <button
          class="btn"
          open-type="getUserInfo"
          type="primary"
          @getuserinfo="bindGetUserInfo"
        >
          授权登录
        </button>
      </view>
    </view>
  </view>
</template>
<script>
export default {
  data() {
    return {};
  },
  components: {},
  methods: {
    // 授权
    bindGetUserInfo(e) {
      let that = this;
      console.log(e);
      if (e.detail.userInfo) {
        that.nickName = e.detail.userInfo.nickName;
        that.nickUrl = e.detail.userInfo.avatarUrl;
        uni.setStorageSync("nickname", e.detail.userInfo.nickName);
        uni.setStorageSync("nickurl", e.detail.userInfo.avatarUrl);
        uni.showLoading({
          title: "正在登陆",
          mask: true,
          duration: 2000,
        });
        setTimeout(function () {
          console.log("aa");
          uni.navigateTo({
            url: "/pages/index/index?id=0",
          });
          uni.hideLoading();
        }, 1800);
      } else {
      }
    },
  },
};
</script>
<style lang="scss" scoped>
.content {
  width: 750rpx;
  height: 100vh;
  position: relative;
  .container {
    width: 100%;
    height: 100%;
    background: #94747e;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1;
    .pageBox {
      padding: 10%;
    }
    .btn {
      width: 100%;
      line-height: 40px;
      color: #ffffff;
      background: #1aad19;
      text-align: center;
      border-radius: 20px;
      margin: auto;
    }
  }
}
</style>
