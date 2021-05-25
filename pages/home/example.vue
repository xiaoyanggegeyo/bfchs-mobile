<template>
  <div class="root">
    <div class="img-box" v-for="(item,index) in exampleList" :key="index" @click="getExampleDeatil(item)">
      <img :src="item.picUrl" alt="" class="img">
      <a href="tel:15628008678" variant="success" class="button">立即联系</a>
    </div>
  </div>
</template>

<script>
  import exampleDeatil from '@/pages/common/example-details.vue';

  export default {
    name: "example",
    components:{exampleDeatil},
    data() {
      return {}
    },
    props: {
      exampleList: {
        type: Array,
        default: function () {
          return [];
        }
      }
    },
    methods: {
      getExampleDeatil(item) {
        this.$axios.post('/commom/getGoodsDetail?goodsId=' + item.id).then(res => {
          if (res.data.code == 200) {
            this.$layer.iframe({
              content: {
                content: exampleDeatil,
                parent: this,
                data: {
                  detailsData: res.data.data
                }
              },
              area: ['80%', '80%'],
              title: res.data.data.subtitle,
              cancel: () => {

              }
            });


          }
        }).catch(err => {

        })
      }
    }
  }
</script>

<style scoped lang="scss">
  .root {
    width: 100%;
    padding-top: 1rem;
    /*padding: .6rem 1rem .6rem .9rem;*/
    display: flex;
    flex-wrap: wrap-reverse;


    .img-box {
      display: flex;
      width: 170px;
      height: 170px;
      padding-right: .3rem;
      margin: 0 auto;
      text-align: center;
      flex-direction: column;
      margin-bottom: .8rem;

      .img {
        display: inline-block;
        border-radius: .5rem;

        width: 100%;
        height: 80%;
      }

      .button {
        background-color: #42bd56;
        font-size: .9rem;
        color: #fff;
        border-radius: .5rem;
        margin: 0 auto;
        margin-top: .5rem;
        width: 6rem;

      }
    }
  }

</style>
