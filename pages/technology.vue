<template>
  <div class="root">
    <Title title="联系我们"/>
    <div class="text">联系人: 刘(先生)</div>
    <div class="text">电话：15208592811</div>
    <div class="text">手机号码：152-0859-2811</div>
    <div class="text">联系邮箱：v185-7517-6400@15dwq.uu.me</div>
    <div class="text">地址: 贵州省贵阳市</div>
  </div>

</template>

<script>
  import {mapState} from 'vuex';
  import Title from '@/pages/common/title';

  if (process.browser) { // 在这里根据环境引入wow.js
    var {WOW} = require('wowjs')
  }

  export default {
    data() {
      return {
        active: 0,

      }
    },
    components: {
      Title
    },
    watch: {
      subNavIndex(newVal, oldVal) {
        this.active = newVal - 1
      }
    },
    computed: {
      ...mapState(['subNavIndex']),
    },
    mounted() {
      this.active = this.subNavIndex == 0 ? 0 : this.subNavIndex - 1
      if (process.browser) {  // 在页面mounted生命周期里面 根据环境实例化WOW
        new WOW({}).init()
      }
    },
    methods: {}
  }
</script>

<style lang="scss" scoped>
  @import '@/assets/styles/variables.scss';

  .root {
    margin-top: 2rem;

    .text {
      padding: 0 2rem;
      line-height: 2.5em;
      color: #666666;
      font-family: 微软雅黑;
    }
  }

  /deep/ .nav-tabs {
    padding: 15px 0;

    .nav-link {
      border-color: transparent;
      font-size: 16px;
      color: #333333;
    }

    .nav-link:hover {
      color: #0056b3;
    }
  }

  .desc {
    line-height: 3.5;
  }

  /deep/ label {
    color: #6c757d !important;
  }

  /deep/ .form-control, /deep/ .custom-select {
    border-radius: 0 !important;
    border-color: #e4eaec !important;
    color: #aaaaaa !important;
  }

  /deep/ .form-control::placeholder, /deep/ .custom-select::placeholder {
    color: #aaaaaa !important;
  }
</style>
