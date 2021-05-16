<template>
  <div class="root">
    <a class="box" href="tel:15208592811">
      <img class="img" :src="navList[0].icon" alt="">
      <div class="text">{{navList[0].text}}</div>
    </a>
    <a class="box" href="sms:15208592811">
      <img class="img" :src="navList[1].icon" alt="">
      <div class="text">{{navList[1].text}}</div>
    </a>
    <a class="box" href="javascript:void(0)" @click="$router.push({path:'/technology'})">
      <img class="img" :src="navList[2].icon" alt="">
      <div class="text">{{navList[2].text}}</div>
    </a>
    <a class="box" href="mqqwpa://im/chat?chat_type=wpa&uin=1716656116&version=1&src_type=web&web_src=oicqzone.com">
      <img class="img" :src="navList[3].icon" alt="">
      <div class="text">{{navList[3].text}}</div>
    </a>

  </div>

</template>

<script>
  export default {
    name: "footer-nav",
    data() {
      return {
        navList: [
          {icon: require('~/static/img/common/dianhua.png'), text: '电话咨询', path: ''},
          {icon: require('~/static/img/common/xinxi.png'), text: '信息咨询', path: ''},
          {icon: require('~/static/img/common/ditu.png'), text: '联系我们', path: ''},
          {icon: require('~/static/img/common/qq.png'), text: 'QQ客服', path: ''}]

      }
    },
    methods: {}
  }
</script>

<style scoped lang="scss">
  .root {
    position: fixed;
    bottom: 0;
    z-index: 2;

    display: flex;
    background-color: #42bd56;
    width: 100%;
    height: 55px;

    .box {
      text-align: center;
      flex: 1;
      display: flex;
      flex-direction: column;


      .img {
        padding-top: .15rem;
        margin: 0 auto;
        flex: 1;
        width: 30px;
        height: 30px;
      }

      .text {
        flex: 1;
        color: #fff;
        line-height: 1.5rem;
        font-size: .5rem;
        text-overflow: ellipsis;
        white-space: nowrap;
        /*padding-top: 2px;*/
      }

    }
  }

</style>
