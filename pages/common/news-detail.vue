<template>
  <div class="root">
    <div class="detail" v-html="this.detailsData.detail"></div>
  </div>

</template>

<script>
  export default {
    name: "news-detail",
    data() {
      return {}
    },
    mounted() {
    },
    props: {
      detailsData: {
        type: Object,
        default: function () {
          return null;
        }
      }
    },
    methods: {}
  }
</script>

<style scoped lang="scss">
  .root {
    width: 100%;
    height: 100%;
    .detail {
      width: 100%;
      height: 98%;
      padding: 0 .5rem;
    }
  }

</style>
