<template>
  <div class="main-container">

    <el-col :gutter="20">
        <el-col :span="4">
          <div class="tab-style grid-content bg-purple">
            <div class="tab">
              <div class="tab-item" v-for="(item,index) in tablist" :key="index">
                <!-- 动态路由 -->
                <nuxt-link tag="div" :to="{path:`/${item.type}`}" class="tab-item-content" @click.native.prevent="gettype(item.type)">{{item.name}}</nuxt-link>
              </div>
            </div>
          </div>
        </el-col>
        <el-col :span="12">
          <div class='article-content'>
            <nuxt-child :articlelist='list' :currenttype='currenttype'></nuxt-child>
          </div>
        </el-col>
        <el-col :span="5">
          <div class="login-container-style">
            <div class="login-container grid-content bg-purple">
              <transition name="fade" mode="out-in">
                <Login @islogin="getloginmsg" v-if="toggle" />
                <Register @islogin="getloginmsg" v-else />
              </transition>
            </div>
          </div>
        </el-col>
      </el-col>
  </div>
</template>

<script>
import ContentType from "@/components/home/contentType";
import Login from "@/components/home/login";
import Register from "@/components/home/register";
export default {
  components: {
    ContentType,
    Register,
    Login
  },
  data() {
    return {
      toggle: true,
      list: [],
      currenttype: "home",
      tablist: [
        { name: "首页", type: "home" },
        { name: "Javascript", type: "javascript" },
        { name: "HTML", type: "html" },
        { name: "Css", type: "css" }
      ]
    }
  },
  methods:{
    // 获取类型并赋值给currenttype
    gettype(type) {
      this.currenttype = type;
      console.log(this.currenttype); 
      if(this.currenttype == 'javascript'){
        this.list = [
          {
            title: "node",
            time: "2012.2.2",
            author: "lee",
            read: 0,
            comments: 12,
            content:
              "简介：JavaScript一种直译式脚本语言，是一种动态类型、弱类型、基于原型的语言，内置支持类型。它的解释器被称为JavaScript引擎，为浏览器的一部分，广泛用于客户端的脚本语言，最早是在HTML（标准通用标记语言下的一个应用）网页上使用，用来给HTML网页增加动态功能。在1995年时，由Netscape公司的Brendan ..."
          },
          {
            title: "node",
            time: "2012.2.2",
            author: "lee",
            read: 0,
            comments: 12,
            content:
              "简介：JavaScript一种直译式脚本语言，是一种动态类型、弱类型、基于原型的语言，内置支持类型。它的解释器被称为JavaScript引擎，为浏览器的一部分，广泛用于客户端的脚本语言，最早是在HTML（标准通用标记语言下的一个应用）网页上使用，用来给HTML网页增加动态功能。在1995年时，由Netscape公司的Brendan ..."
          },
          {
            title: "node",
            time: "2012.2.2",
            author: "lee",
            read: 0,
            comments: 12,
            content:
              "简介：JavaScript一种直译式脚本语言，是一种动态类型、弱类型、基于原型的语言，内置支持类型。它的解释器被称为JavaScript引擎，为浏览器的一部分，广泛用于客户端的脚本语言，最早是在HTML（标准通用标记语言下的一个应用）网页上使用，用来给HTML网页增加动态功能。在1995年时，由Netscape公司的Brendan ..."
          }
        ];
      }
    },
    // 获取传递过来的登录切换信息
    getloginmsg(msg) {
      this.toggle = msg;
    }
  },
  created:function(){
      this.$router.push('/home'); // 页面加载时跳转
    },
  watch: {
    // 这里就重新调取关于相关类型的文章
    currenttype(l, lk) {
      if (l == "javascript") {
        
      }
    }
  },
  mounted() {
   
  }
};
</script>

<style lang="scss">
@import "@/assets/css/main/index.scss";
</style>
