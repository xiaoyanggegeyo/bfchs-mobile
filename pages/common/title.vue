<template>
  <div class="root">
    <div class="left-box">{{title}}</div>
    <div class="right-box">
      <slot name="title-nav"></slot>
    </div>
  </div>
</template>

<script>
  export default {
    name: "title",
    props: {
      title: {
        type: String,
        default: ''
      }
    }
  }
</script>

<style scoped lang="scss">
  .root {
    height: 46px;
    padding-top: .3rem;
    padding-bottom: 1rem;
    padding-right: .5rem;
    display: flex;
    border-bottom: 1px solid #ccc;

    .left-box {
      flex: 1;
      text-align: left;
      color: #42bd56;
      font-size: 1.2rem;
      line-height: 2.6rem;
      border-left: .5rem solid #42bd56;
      padding-left: .5rem;

    }

    .right-box {
      flex: 1;
      text-align: right;
      color: #42bd56;
      font-size: 1.8rem;
      line-height: 2.8rem;

    }
  }

</style>
