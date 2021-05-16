<template>
  <section class="py-5 wrapper">
    <Title title="案例展示"/>
    <div class="container">
      <Example :exampleList="exampleList"/>
    </div>
  </section>
</template>

<script>
  import {mapState} from 'vuex'

  if (process.browser) { // 在这里根据环境引入wow.js
    var {WOW} = require('wowjs')
  }

  import Title from '@/pages/common/title';
  import Example from '@/pages/home/example';

  export default {
    components: {Title, Example},
    data() {
      return {
        active: null,
        list: [],
        tabList: ['全部', '云计算', '大数据'],
        exampleList: [
          {
            icon: require('~/static/img/example/1.jpg')
          }, {
            icon: require('~/static/img/example/2.jpg')
          }, {
            icon: require('~/static/img/example/3.jpg')
          }, {
            icon: require('~/static/img/example/4.jpg')
          },
          {
            icon: require('~/static/img/example/5.jpg')
          }, {
            icon: require('~/static/img/example/6.jpg')
          }, {
            icon: require('~/static/img/example/7.jpg')
          }, {
            icon: require('~/static/img/example/8.jpg')
          }, {
            icon: require('~/static/img/example/9.jpg')
          }, {
            icon: require('~/static/img/example/10.jpg')
          }
        ]
      }
    },
    watch: {
      subNavIndex(newVal, oldVal) {
        this.active = newVal
        this.getList()
      }
    },
    computed: {
      ...mapState(['subNavIndex']),
    },
    mounted() {
      this.active = this.subNavIndex
      this.getList()
    },
    methods: {
      // 筛选列表
      getList() {
        switch (Number(this.active)) {
          case 0:
            this.list = this.productList;
            break;
          case 1:
            this.list = this.productList.slice(0, 2);
            break;
          case 2:
            this.list = this.productList.slice(2)
        }
        this.$nextTick(() => {
          if (process.browser) {
            new WOW({}).init()
          }
        })
      },
      // 点击筛选
      handleTabClick(index) {
        this.$store.commit('setSubNavIndex', index)
      },
      // 点击查看详情
      handleDetail(id) {
        this.$router.push(`/product/${id}`)
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import '@/assets/styles/variables.scss';

  .wrapper {
    background: #f2f2f2;
  }

  .card {
    border: none;
  }

  /deep/ .list-group-item {
    border-color: transparent;
    border-radius: 0;
  }

  /deep/ .list-group-item.active {
    background: $theme-color;
  }

  /deep/ .list-group-item:hover {
    cursor: pointer;
  }
</style>
