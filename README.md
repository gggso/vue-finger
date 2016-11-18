# vue-finger
基于腾讯AlloyFinger的vue 2.0手势插件  AlloyFinger：http://alloyteam.github.io/AlloyFinger/

所有手势事件<br>
v-tap：点击事件<br>
v-singleTap：单击事件，和tap的区别是相差250ms<br>
v-longTap：长按事件，当点击时长超过750ms时候触发<br>
v-doubleTap：双击事件<br>
v-pressMove：拖拽移动事件<br>
v-multipointStart：多点触控事件开始事件<br>
v-multipointEnd：多点触控事件结束事件<br>
v-swipe：滑动事件<br>
v-rotate：旋转事件<br>
v-pinch：缩放事件<br>
<br>
使用示例：<br>
见fingerDemo,在项目中使用的时候，在main.js中导入、vue.use()，然后在子组件中就可以直接用v-tap="{methods：func , arg: args}"的方式使用
