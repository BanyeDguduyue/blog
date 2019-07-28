<template>
  <el-container>
    <el-header style="height:20vh">
      <div class="header-bg">半夜的孤独月</div>
      <div class="wall"></div>
    </el-header>
    <el-main center='false'>
      <nuxt/>
    </el-main>
    <el-footer style="height:10vh">Footer</el-footer>
  </el-container>
</template>

<script>

export default {
  data() {
    return {

    };
  },
  components: {
  },
  methods: {
    
  }
};
</script>

<style lang='scss'>
@import "@/assets/css/layout/index.scss";
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
