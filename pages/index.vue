<template>
  <div class="main-container">
    <el-row :gutter="20">
      <el-col :span="18">
        <div class="grid-content bg-purple">
          11
        </div>
      </el-col>
      <el-col :span="6">
        <div class="login-container grid-content bg-purple">
          当前是{{currentname}}分区
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import Login from "@/components/home/login";
export default {
  props:['currentname'],
  components: {
    
  },
  watch:{
    currentname(l,lk){
      console.log(l,lk);
      
    }
  },
  mounted(){
    setTimeout(()=>{
      console.log(this.currentname);
    }, 1000) 
  }
};
</script>

<style lang="scss">
@import "@/assets/css/main/index.scss";
</style>
