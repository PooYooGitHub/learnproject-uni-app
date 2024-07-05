<template>
	<view class="my-search-container" :style="{'background-color': bgcolor}">
	  <view class="my-search-box" :style="{'border-radius': radius + 'px'}" @click="searchBoxHandler">
		<uni-icons type="search" size="17"></uni-icons>
		<text class="placeholder">搜索</text>
	  </view>
	</view>
</template>

<script>
export default {
  name: "my-search",
  data() {
    return {
      wh: 0
    };
  },
  mounted() {
    const sysInfo = uni.getSystemInfoSync();
    // 可用高度 = 屏幕高度 - navigationBar高度 - tabBar高度 - 自定义的search组件高度
    this.wh = sysInfo.windowHeight - 50;
  },
  props: {
    // 背景颜色
    bgcolor: {
      type: String,
      default: '#C00000'
    },
    // 圆角尺寸
    radius: {
      type: Number,
      // 单位是 px
      default: 18
    }
  },
  methods: {
    // 点击了模拟的 input 输入框
    searchBoxHandler() {
      // 触发外界通过 @click 绑定的 click 事件处理函数
	  // 通过 $emit 方法，子组件可以通知父组件发生了某个事件。在这个例子中，子组件触发了一个名为 'click' 的事件。
      this.$emit('click');
    }
  }
}
</script>

<style lang="scss">
// .my-search-container {
//   background-color: #c00000;
//   height: 50px;
//   padding: 0 10px;
//   display: flex;
//   align-items: center;
// }

// .my-search-box {
//   height: 36px;
//   background-color: #ffffff;
//   border-radius: 15px;
//   width: 100%;
//   display: flex;
//   align-items: center;
//   justify-content: center;

//   .placeholder {
//     font-size: 15px;
//     margin-left: 5px;
//   }
// }
</style>