<template>
  <div class="finger-demo">
    <img class="finger-demo-img" src="../../../assets/logo.png" :style="imgStyle" 
    	v-tap="tap"
    	v-singleTap="singleTap"
    	v-longTap="longTap"
    	v-doubleTap="doubleTap"
    	v-pressMove="pressMove"
    	v-swipe="swipe"
    	v-rotate="rotate" 
    	v-multipointStart="multipointStart" 
    	v-multipointEnd="multipointEnd"
    	v-pinch="pinch"/>
    <div>{{ msg }}</div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      left: 0,
      top: 0,
      scale: 1,
      angle: 0,
      initScale: 1,
      msg: ''
    }
  },
  computed: {
    imgStyle () {
      var self = this
      var tempObj = {
        transform: 'translate3d(' + self.left + 'px, ' + self.top + 'px, 0) scale(' + self.scale + ') rotate(' + self.angle + 'deg)'
      }
      return tempObj
    }
  },
  methods: {
    tap (e) {
      var self = this
      self.msg = 'tap'
    },
    singleTap (e) {
      var self = this
      self.msg = 'singleTap'
    },
    longTap (e) {
      var self = this
      self.msg = 'longTap'
    },
    doubleTap (e) {
      var self = this
      self.msg = 'doubleTap'
    },
    rotate (e) {
      var self = this
      self.msg = 'rotate'
      self.angle += e.angle
    },
    pressMove (e) {
      var self = this
      self.msg = 'pressMove'
      self.left += e.deltaX
      self.top += e.deltaY
    },
    swipe (e) {
      var self = this
      self.msg = 'swipe'
    },
    multipointStart: function (e) {
      var self = this
      self.msg = 'multipointStart'
      self.initScale = self.scale
    },
    multipointEnd: function (e) {
      var self = this
      self.msg = 'multipointEnd'
    },
    pinch (e) {
      var self = this
      self.msg = 'pinch'
      self.scale = self.initScale * e.scale
    }
  }
}
</script>
<style>
.finger-demo{width:100%;text-align:center;}
.finger-demo-img{width:80%;}
</style>