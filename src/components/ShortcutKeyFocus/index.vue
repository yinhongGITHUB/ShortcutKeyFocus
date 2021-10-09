<template>
  <div
    :class="[{ select: selectCard }, parentStyle]"
    @click="handleDevByClicking"
  >
    <slot></slot>
    <div class="hello">
      这里是快捷键焦点组件（一般不显示在页面上，使用时请清空）
    </div>

    <input readonly="readonly" @keyup.stop="handlePressTheShortcutKey" id="myInput" />
  </div>
</template>
<script>
export default {
  props: {
    keyArr: Array,
    keyStyle: {
      default: "",
    },
  },
  data() {
    return {
      parentStyle: undefined,
      selectCard: false, // true为选中，false为不选中
    };
  },
  mounted() {
    let letterReg = /[a-zA-Z]/;
    let figureReg = /[0-9]/;
    this.keyArr.forEach((item) => {
      if (!letterReg.test(item)&&!figureReg.test(item)) {// 既不是数字也不是字母
        throw "请输入正确的数组";
      }
    });
  },
  methods: {
    // 点击组件时，获取焦点，便于后续快捷键触发事件
    handleDevByClicking() {
      let myInput = document.getElementById("myInput");
      this.selectCard = !this.selectCard;
      if (this.selectCard) {
        myInput.focus();
        this.parentStyle = this.keyStyle;
      } else {
        myInput.blur();
        this.parentStyle = "";
      }
    },
    handlePressTheShortcutKey(e) {
      let myInput = document.getElementById("myInput");
      myInput.value = "";
      let newKeyArr = this.keyArr.map((item) => {
        // 统一转换成小写字母
        if (typeof item === "number") {
          return String.fromCharCode(item);
        }else if(typeof item === "string"){
          return item
        }
        return item;
      });
      let str = e.code;
      console.log("这里是子组件",str[str.length - 1].toLocaleLowerCase());
      if (newKeyArr.includes(str[str.length - 1].toLocaleLowerCase())) {
        // 返回的是当前按下键的小写字母
        this.$emit("handlechange", str[str.length - 1].toLocaleLowerCase()); // 快捷键触发父组件的方法
      }
    },
  },
};
</script>
<style scoped lang='less'>
#myInput {
  position: absolute;
  left: -9999px;
}
.select {
  border: 1px solid red;
}
.hello {
  color: red;
}
</style>