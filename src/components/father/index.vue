<template>
  <div>
    <ShortcutKeyFocus
      :keyArr="addKeyArr"
      @handlechange="handlechange"
      :keyStyle="abc"
      >
      <div id="box"> 这里是父级组件代码</div>
     
      </ShortcutKeyFocus>
  </div>
</template>

<script>
import ShortcutKeyFocus from "../ShortcutKeyFocus/index.vue";
export default {
  data() {
    return {
      title: "这里是父组件",
      abc: "abc", // 你想传入的任何样式
      addKeyArr: ["a", "d",97,98], // 你想用哪些快捷键触发你期望的事件
    };
  },
  components: {
    ShortcutKeyFocus,
  },
  methods: {
    handlechange(code) {
      console.log("进入了父组件",code);
      // todo........写你的业务逻辑代码
    },
  },
};
</script>

<style lang="less" scoped>
#box{
  width: 500px;
  height: 400px;
  background: yellow;
}
.abc {
  border: 1px solid blue;
}
</style>