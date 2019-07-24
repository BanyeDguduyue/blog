<template>
  <el-container>
    <el-header style="height:20vh">
      <div class="header-bg">半夜的孤独月</div>
      <div class="wall"></div>
    </el-header>
    <el-main>
      <el-col :gutter="20">
        <el-col :span="1">
          <div class="tab-style grid-content bg-purple">
            <div class="tab">
              <div class="tab-item" v-for="(item,index) in tablist" :key="index">
                <div class="tab-item-content" @click="gettype(item.name)">{{item.name}}</div>
              </div>
            </div>
          </div>
        </el-col>
        <el-col :span="18">
          <div class="">
            <nuxt-child :currentname='this.currentname' />
          </div>
        </el-col>
        <el-col :span="5">
          <div class="login-container-style">
            <div class="login-container grid-content bg-purple">
            <!-- <Login/> -->
            <Register/>
          </div>
          </div>
        </el-col>
      </el-col>
    </el-main>
    <el-footer style="height:10vh" @click.native="abc">Footer</el-footer>
  </el-container>
</template>

<script>
import Login from "@/components/home/login";
import Register from "@/components/home/register";
export default {
  data() {
    return {
      currentname: "首页",
      tablist: [
        { name: "首页",type:'home'},
        { name: "Javascript",type:'javascript'},
        { name: "HTML",type:'html'},
        { name: "Css",type:'css'}
      ]
    };
  },
  components: {
    Login,
    Register
  },
  methods: {
    abc(){
      console.log(this.currentname);
    },
    gettype(name){
      this.currentname = name
    }
  }
};
</script>

<style lang='scss'>
@import "@/assets/css/layout/index.scss";
</style>
