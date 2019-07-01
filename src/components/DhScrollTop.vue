<template>
  <span
    @click="switchFun"
    class="dh-scroll-top"
    :style="{width:`${size}px`, 'line-height':`${size}px`,bottom:`${gap}px`,right:`${gap}px`}"
  >&lt;</span>
</template>
<script>
export default {
  name: "scroll-top",
  props: {
    /**
     * @type
     * 0 => document.body.scrollTop = 0
     * 1 => ele.scrollIntoView()
     * 2 => window.scrollBy(0,offset)
     */
    type: {
      type: Number,
      default: 0
    },
    size: {
      type: Number,
      default: 40
    },
    gap: {
      type: Number,
      default: 40
    }
  },
  methods: {
    switchFun() {
      switch (this.type) {
        case 0:
          this.byScrollTop();
          break;
        case 1:
          this.byScrollIntoView();
          break;
        case 2:
          this.byScrollBy();
          break;
        default:
          this.byScrollTop();
      }
    },
    byScrollTop() {
      let oldVal = document.documentElement.scrollTop;
      if (!oldVal) return;
      let timer = setInterval(() => {
        document.documentElement.scrollTop = oldVal = oldVal - 50;
        if (oldVal <= 0) {
          window.clearInterval(timer);
          console.log("finish");
        }
      });
    },
    byScrollIntoView() {
      document.documentElement.scrollIntoView({
        behavior: "smooth"
      });
      console.log("finish");
    },
    byScrollBy() {
      window.scrollBy(0, -document.documentElement.scrollTop);
      console.log("finish");
    }
  }
};
</script>
<style lang="less" scoped>
.dh-scroll-top {
  position: fixed;
  background-color: #fff;
  transform: rotate(90deg);
  font-size: 18px;
  color: #999;
  cursor: pointer;
  border-radius: 50%;
  text-align: center;
  transition: all 0.5s;
  box-shadow: 0 0 8px 1px rgba(0, 0, 0, 0.14);
  &:hover {
    color: #bbb;
    box-shadow: 0 0 8px 1px rgba(0, 0, 0, 0.17);
  }
}
</style>
