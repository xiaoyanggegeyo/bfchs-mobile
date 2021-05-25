<template>
  <section class="py-5 wrapper">
    <Title title="汽车交易"/>
    <div class="container">
      <Example :exampleList="exampleList"/>
    </div>
  </section>
</template>

<script>
  import {mapState} from 'vuex'
  import Title from '@/pages/common/title';
  import Example from '@/pages/home/example';

  if (process.browser) { // 在这里根据环境引入wow.js
    var {WOW} = require('wowjs')
  }


  export default {
    components: {Title, Example},
    data() {
      return {
        active: null,
        list: [],
        tabList: ['全部', '云计算', '大数据'],
        exampleList: []
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
      this.getList();
      this.getExampleList();
    },
    methods: {
      /**
       * 获取案例数据列表
       */
      getExampleList() {
        this.$axios.post('/commom/getGoodsList?pageNo=1&pageSize=100&classId=1').then(res => {
          this.exampleList = res.data.data.items;
        })
      },
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
