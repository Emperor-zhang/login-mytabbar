<template>
  <view class="content">
    <hans-tabber
      :list="list"
      style="position: fixed; bottom: 0; width: 100%; left: 0; right: 0"
      @tabChange="tabChange"
    ></hans-tabber>
    <index v-if="num == 0"></index>
    <list v-else-if="num == 1"></list>
    <mine v-else></mine>
  </view>
</template>

<script>
import hansTabber from "@/components/hans-tabbar/hans-tabbar.vue";
import index from "@/components/index/index.vue";
import list from "@/components/list/index.vue";
import mine from "@/components/mine/index.vue";
export default {
  data() {
    return {
      list: [
        {
          text: "首页",
          iconPath: "../../static/index.png",
          selectedIconPath: "../../static/index-on.png",
        },
        {
          text: "列表",
          iconPath: "../../static/list.png",
          selectedIconPath: "../../static/list-on.png",
        },
        {
          text: "我的",
          iconPath: "../../static/mine.png",
          selectedIconPath: "../../static/mine-on.png",
        },
      ],
      num: 0,
    };
  },
  onLoad(e) {
    this.num = e.id;
  },
  methods: {
    tabChange(index) {
      this.num = index;
    },
  },
  components: {
    hansTabber,
    index,
    list,
    mine,
  },
};
</script>

<style lang="scss" scoped>
.content {
  width: 100%;
  height: 100%;
  .canvasBox {
    width: 100%;
    height: 100%;
    .content-img {
      width: 100%;
      height: 100%;
      image {
        width: 100%;
      }
    }
  }
}
</style>
