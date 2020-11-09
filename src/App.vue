<script>
export default {
  onLaunch: function () {
    let that = this;
    console.log("App Launch");
    // 检验、登录
    uni.checkSession({
      success: function (r) {
        //session_key 未过期，并且在本生命周期一直有效
        uni.getUserInfo({
          success: function (result) {
            console.log("已授权", result);
          },
        });
      },
      fail: function () {
        //session_key 已经失效，需要重新执行登录流程
        // 是否已授权
        uni.getSetting({
          success: function (res) {
            if (res.authSetting["scope.userInfo"]) {
              uni.getUserInfo({
                success: function (result) {
                  console.log(result);
                },
              });
            } else {
              uni.navigateTo({
                url: "/pages/login/index",
              });
            }
          },
        });
      },
    });
  },
  onShow: function () {
    console.log("App Show");
  },
  onHide: function () {
    console.log("App Hide");
  },
};
</script>

<style>
/*每个页面公共css */
@import url("./static/styles/base.wxss");
</style>
