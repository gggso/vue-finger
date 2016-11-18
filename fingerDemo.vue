<template>
  <div class="finger-demo">
    <img class="finger-demo-img" src="../../../assets/logo.png" :style="imgStyle" 
    	v-tap="{methods: tap, arg: {index:1,item:'tap'}}"
    	v-singleTap="{methods: singleTap, arg: {index:2,item:'singleTap'}}"
    	v-longTap="{methods: longTap, arg: {index:3,item:'longTap'}}"
    	v-doubleTap="{methods: doubleTap, arg: {index:4,item:'doubleTap'}}"
    	v-pressMove="{methods: pressMove, arg: {index:5,item:'pressMove'}}"
    	v-swipe="{methods: swipe, arg: {index:6,item:'swipe'}}"
    	v-rotate="{methods: rotate, arg: {index:7,item:'rotate'}}" 
    	v-multipointStart="{methods: multipointStart, arg: {index:8,item:'multipointStart'}}" 
    	v-multipointEnd="{methods: multipointEnd, arg: {index:9,item:'multipointEnd'}}"
    	v-pinch="{methods: pinch, arg: arg}"/>
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
      msg: '',
      arg: {index: 10, item: 'pinch'}
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
    tap (e, args) {
      var self = this
      self.msg = 'tap'
      console.log('tap index:' + args.index + 'item:' + args.item)
    },
    singleTap (e, args) {
      var self = this
      self.msg = 'singleTap'
      console.log('tap index:' + args.index + 'item:' + args.item)
    },
    longTap (e, args) {
      var self = this
      self.msg = 'longTap'
      console.log('tap index:' + args.index + 'item:' + args.item)
    },
    doubleTap (e, args) {
      var self = this
      self.msg = 'doubleTap'
      console.log('tap index:' + args.index + 'item:' + args.item)
    },
    rotate (e, args) {
      var self = this
      self.msg = 'rotate'
      self.angle += e.angle
      console.log('tap index:' + args.index + 'item:' + args.item)
    },
    pressMove (e, args) {
      var self = this
      self.msg = 'pressMove'
      self.left += e.deltaX
      self.top += e.deltaY
      console.log('tap index:' + args.index + 'item:' + args.item)
    },
    swipe (e, args) {
      var self = this
      self.msg = 'swipe'
      console.log('tap index:' + args.index + 'item:' + args.item)
    },
    multipointStart: function (e, args) {
      var self = this
      self.msg = 'multipointStart'
      self.initScale = self.scale
      console.log('tap index:' + args.index + 'item:' + args.item)
    },
    multipointEnd: function (e, args) {
      var self = this
      self.msg = 'multipointEnd'
    },
    pinch (e, args) {
      var self = this
      self.msg = 'pinch'
      self.scale = self.initScale * e.scale
      console.log('tap index:' + args.index + 'item:' + args.item)
    }
  }
}
</script>
<style>
.finger-demo{width:100%;text-align:center;}
.finger-demo-img{width:80%;}
</style>