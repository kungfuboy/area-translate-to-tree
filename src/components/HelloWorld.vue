<template>
  <div class="sliderRoot">
    <transition-group tag="ul" class='slide-ul' name="list">
        <li v-for="(item,index) in list" 
            :key="index" 
            :style="{backgroundImage: `url(${item})`}"
            v-show="index===activeIndex">
        </li>
    </transition-group>
  </div>
</template>

<script>
export default {
  props: ['imgList', 'showTime'],
  data() {
    return {
      list: this.imgList,
      activeIndex: 0,
      timer: ''
    }
  },
  methods: {
    change(index) {
      this.activeIndex = index
    },
    autoPlay() {
      this.activeIndex++
      if (this.activeIndex > this.list.length - 1) {
        this.activeIndex = 0
      }
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.timer = setInterval(() => {
        this.autoPlay()
      }, this.showTime)
    })
  }
}
</script>

<style lang="less" scoped>

@time: 2s;

.sliderRoot {
  height: 100vh;
  width: 100vw;
  overflow: hidden;
}

.slide-ul {
  position: relative;
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  li {
    position: absolute;
    width: 100%;
    height: 100%;
    background-position: center center;
    background-size: cover;
    background-repeat: no-repeat;
    list-style: none;
    padding: 0;
  }
}

.list-enter-to {
  transition: all @time ease;
  transform: translateX(0);
}

.list-leave-active {
  transition: all @time ease;
  transform: translateX(-100vw);
}

.list-enter {
  transform: translateX(100vw);
}

.list-leave {
  transform: translateX(0);
}
</style>
