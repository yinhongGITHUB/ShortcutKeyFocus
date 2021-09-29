# 快捷键焦点组件

问：什么叫快捷键焦点组件？
答：可以让某个组件组件代码在没有input框的情况下获取焦点，并且按下键盘指定快捷键（如：A/D）触发指定事件的公共组件

# UI

![例子](https://github.com/yinhongGITHUB/ShortcutKeyFocusComponentPackage/blob/main/src/components/ShortcutKeyFocus/UI.png)

# 如何使用

```js
     <ShortcutKeyFocus
      :keyArr="addKeyArr"
      @handlechange="handlechange"
      :style="abc"
      >
      </ShortcutKeyFocus>
```
# 效果演示
 
![image](https://github.com/yinhongGITHUB/ShortcutKeyFocusComponentPackage/blob/main/src/components/ShortcutKeyFocus/resultsShow.gif)

# 使用步骤：

1.引入快捷键焦点组件

2.将你的所有业务代码用*快捷键焦点组件*包起来

3.快捷键焦点组件API

# API

参数|说明|类型|默认值
---|:--:|:---:|---:
keyArr|哪些快捷键生效|string[]/number[]|-
handlechange|键盘按下指定快捷键触发的函数，里面的参数是a-z小写字母| function(code: a-z)|- 
keyStyle|修改边框的样式|类名即可|-



