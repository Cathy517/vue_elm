<template>
  <header id="head_top">
    <slot name="logo"></slot>
    <slot name="search"></slot>
    <section class="head_goback" v-if="goBack" @click="$router.go(-1)">
      <svg width="100%" height="100%" xmlns="http://www.w3.org/2000/svg" version="1.1">
        <polyline points="12,18 4,9 12,0" style="fill:none;stroke:rgb(255,255,255);stroke-width=2"></polyline>
      </svg>
    </section>
    <router-link to="login" v-if="signinUp" class="head_login">
      <svg class="user_avatar" v-if="userInfo">
        <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#user"></use>
      </svg>
      <span class="login_span" v-else>登录|注册</span>
    </router-link>
    <section class="title_head ellipsis" v-if="headTitle">
      <span class="title_text" >{{headTitle}}</span>
    </section>
    <slot name="edit"></slot>
    <slot name="msite-title"></slot>
    <slot name="changecity"></slot>
    <slot name="changeLogin"></slot>
  </header>
</template>
<script>
export default {
  props:['signinUp','headTitle','goBack'],
  data() {
    return {
      userInfo:false
    };
  }
};
</script>
<style lang="scss" scoped>
@import '../../style/mixin';
#head_top{
  background: $blue;
  position: fixed;
  z-index: 100;
  left: 0;
  top: 0;
  @include wh(100%,92px);
}
.head_goback{
  left: 18px;
  @include wh(28px,46px);
  line-height: 128px;
  margin-left: 18px;
}
.head_login{
  right: 26px;
  @include sc(30px,#fff);
  @include ct;
  .login_span{
    color: #fff;
  }
  .user_avatar{
    fill: #fff;
    @include wh(37.5px,37.5px)
  }
}
.title_head{
  @include center;
  width: 50%;
  color: #fff;
  text-align: center;
  .title_text{
    @include sc(37.5px,#fff);
    text-align: center;
    font-weight: bold;
  }
}
</style>
