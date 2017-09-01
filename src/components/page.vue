<template>
  <swiper :options="swiperOption" :not-next-tick="notNextTick" ref="mySwiper">
    <!-- slides -->
    <swiper-slide class="a1">
      <span>1</span>
      I'm Slide 1
    </swiper-slide>
    <swiper-slide class="a2">
      <span>2</span>
      I'm Slide 2
    </swiper-slide>
    <swiper-slide class="a3">
      <span>3</span>
      I'm Slide 3
    </swiper-slide>
    <swiper-slide class="a4">
      <span>4</span>
      I'm Slide 4
    </swiper-slide>
    <swiper-slide class="a5">
      <span>5</span>
      I'm Slide 5
    </swiper-slide>
    <swiper-slide class="a6">
      <span>6</span>
      I'm Slide 6
    </swiper-slide>
    <swiper-slide class="a7">
      <span>7</span>
      I'm Slide 7
    </swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
    <div class="swiper-button-prev" slot="button-prev"></div>
    <div class="swiper-button-next" slot="button-next"></div>
    <div class="swiper-scrollbar"   slot="scrollbar"></div>
  </swiper>
</template>

<script>
import { swiper, swiperSlide } from 'vue-awesome-swiper'

export default {
  name: 'page',
  data () {
    return {
      // notNextTick是一个组件自有属性，如果notNextTick设置为true，组件则不会通过NextTick来实例化swiper，
      // 也就意味着你可以在第一时间获取到swiper对象，假如你需要刚加载遍使用获取swiper对象来做什么事，那么这个属性一定要是true
      notNextTick: true,
      swiperOption: {
        // swiper optionss 所有的配置同swiper官方api配置
        notNextTick: true,
        autoplay: 3000,
        direction: 'vertical',
        grabCursor: true,
        setWrapperSize: true,
        autoHeight: true,
        pagination: '.swiper-pagination',
        paginationClickable: true,
        prevButton: '.swiper-button-prev',
        nextButton: '.swiper-button-next',
        scrollbar: '.swiper-scrollbar',
        mousewheelControl: true,
        observeParents: true,
        // 如果自行设计了插件，那么插件的一些配置相关参数，也应该出现在这个对象中，如下debugger
        debugger: true,
        // swiper的各种回调函数也可以出现在这个对象中，和swiper官方一样
        onTransitionStart (swiper) {
          console.log(swiper)
        }
      }
    }
  },
  // 如果你需要得到当前的swiper对象来做一些事情，你可以像下面这样定义一个方法属性来获取当前的swiper对象，同时notNextTick必须为true
  computed: {
    swiper () {
      return this.$refs.mySwiper.swiper
    }
  },
  mounted () {
    // 然后你就可以使用当前上下文内的swiper对象去做你想做的事了
    // console.log('this is current swiper instance object', this.swiper)
    // this.swiper.slideTo(3, 1000, true)
  },
  components: {
    swiper, swiperSlide
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less">
@import '../assets/page';

.swiper-container, .swiper-wrapper, .swiper-slide {
  width: 100%;
  height: 100%;
}
.swiper-container {
  position: relative;
}
.swiper-slide {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
  color: #666;
  span {
    position: absolute;
    top: 10%;
    font-size: 50px;
    transition: all .8s ease .2s;
  }
  &.swiper-slide-active span {
    color: #eee;
    visibility: visible;
    transform: none;
    opacity: 1;
  }
}
.swiper-pagination {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 10px;
  text-align: center;
  font-size: 0;
  span {
    display: inline-block;
    width: 8px;
    height: 8px;
    margin: 0 3px;
    background: rgba(151,151,151,.25);
    border-radius: 50%;
    overflow: hidden;
  }
  .swiper-pagination-bullet-active {
    background: rgba(214,60,23,.5);
  }
}
.swiper-scrollbar {
  position: absolute;
  right: 3px;
  top: 0.5%;
  width: 3px;
  height: 99%;
  border-radius: 5px;
  background: rgba(255,255,255,.2);
  overflow: hidden;
  .swiper-scrollbar-drag {
    width: 100%;
    height: 100%;
    position: relative;
    border-radius: 5px;
    overflow: hidden;
    left: 0;
    top: 0;
    background: rgba(214,60,23,.5);
  }
}
</style>
