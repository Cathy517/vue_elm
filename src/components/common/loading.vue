<template>
  <div class="loading_container">
    <div class="load_img" :style="{backgroundPositionY:-(positionY%7)*1.6+'rem'}"></div>
    <svg class="load_ellipse" xmlns="http://www.w3.org/2000/svg" version="1.1">
      <ellipse cx="26" cy="10" rx="26" ry="10" style="fill:#ddd;stroke:none" />
    </svg>
  </div>
</template>

<script>
export default {
  data() {
    return {
      positionY: 0,
      timer: null
    };
  },
  mounted() {
    this.timer = setInterval(() => {
      this.positionY++;
    }, 600);
  },
  beforeDestroy() {
    clearInterval(this.timer);
  }
};
</script>
<style lang='scss' scoped>
@import "../../style/mixin";
@keyframes load {
  0% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-50px);
  }
  100% {
    transform: translateY(100px);
  }
}
@keyframes ellipse {
  0% {
    transform: scale(1)
  }
  50% {
    transform: scale(0.3)
  }
  100% {
    transform: scale(1)
  }
}
.loading_container{
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  @include wh(118px,118px);
  z-index: 2;
  .load_img{
    @include wh(100%,100%);
    background: url('~../../images/icon_loading.png') no-repeat 0 0;
    background-size: 118px auto;
    transform: translateY(0px);
    animation: load .6s infinite ease-in-out;
    position: relative;
    z-index: 11;
  }
  .load_ellipse{
    position: absolute;
    @include wh(122px,103px);
    top: 103px;
    left: 9px;
    z-index: 10;
    animation: ellipse .6s infinite ease-in-out;
  }
}
</style>