<template>
  <el-form :model="ruleForm" status-icon :rules="rules" ref="ruleForm" class="demo-ruleForm">
    <el-form-item label="账号" prop="account">
      <el-input type="text" v-model="ruleForm.account" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="密码" prop="pass">
      <el-input type="password" v-model="ruleForm.pass" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="确认密码" prop="checkPass">
      <el-input type="password" v-model="ruleForm.checkPass" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item>
      <div class="noaccount">
        已有账号?
        <span @click="tologin">立即登陆</span>
      </div>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="submitForm('ruleForm')">注册</el-button>
      <el-button @click="resetForm('ruleForm')">重置</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
export default {
  data() {
    var validatePass = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("请输入密码"));
      } else {
        if (this.ruleForm.checkPass !== "") {
          this.$refs.ruleForm.validateField("checkPass");
        }
        callback();
      }
    };
    var validatePass2 = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("请再次输入密码"));
      } else if (value !== this.ruleForm.pass) {
        callback(new Error("两次输入密码不一致!"));
      } else {
        callback();
      }
    };
    const checkAccount = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("请输入账号"));
      }
    };
    return {
      ruleForm: {
        account: "",
        pass: "",
        checkpass: ""
      },
      rules: {
        checkPass: [{ validator: validatePass2, trigger: "blur" }],
        pass: [{ validator: validatePass, trigger: "blur" }],
        account: [{ validator: checkAccount, trigger: "blur" }]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    },
    // 传递信息切换登录注册
    tologin(){
      this.$emit('islogin',true)
    }
  }
};
</script>

<style lang="scss">
@import "@/assets/css/login/login.scss";
</style>