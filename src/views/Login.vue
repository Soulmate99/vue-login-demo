<template>
  <div>
    <el-form ref="loginForm" :model="loginForm" :rules="rules" class="loginForm">
      <h3 class="loginTitle">Login</h3>
      <!--用户名输入框-->
      <el-form-item prop="username">
        <el-input v-model="loginForm.username"
                  auto-complete="false"
                  placeholder="请输入用户名"
                  type="text">
        </el-input>
      </el-form-item>
      <!--密码输入框-->
      <el-form-item prop="password">
        <el-input v-model="loginForm.password"
                  auto-complete="false"
                  placeholder="请输入密码"
                  type="password">
        </el-input>
      </el-form-item>
      <!--验证码输入框-->
      <el-form-item prop="code">
        <el-input v-model="loginForm.code"
                  auto-complete="false"
                  placeholder="点击图片更换验证码"
                  style="width: 250px;margin-right: 10px"
                  type="password">
        </el-input>
        <!--验证码图片-->
        <img :src="captchaUrl">
      </el-form-item>
      <!--功能区-->
      <el-checkbox v-model="checked" class="Remember">记住我</el-checkbox>
      <el-button style="width: 100%" type="primary" @click="submitLogin">登录</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      captchaUrl: '',
      loginForm: {
        username: 'admin',
        password: '123456',
        code: ''
      },
      checked: true,
      rules: {
        username: [{required: true, message: '请输入用户名', trigger: 'blur'}],
        password: [{required: true, message: '请输入密码', trigger: 'blur'}],
        code: [{required: true, message: '请输入验证码', trigger: 'blur'}]
      }
    }
  },
  methods: {
    submitLogin() {
      this.$refs.loginForm.validate((valid) => {
        if (valid) {
          alert('submit!');
        } else {
          this.$message.error('请输入所有字段');
          // console.log('error submit!!');
          return false;
        }
      });
    }
  }
}
</script>

<style scoped>
.loginForm {
  border-radius: 15px;
  background-clip: padding-box;
  margin: 180px auto;
  width: 350px;
  padding: 15px 35px 15px 35px;
  background: white;
  border: 1px solid #eaeaea;
  box-shadow: 0 0 25px #cac6c6;
}

.loginTitle {
  margin: 0 auto 40px auto;
  text-align: center;
}

.Remember {
  text-align: left;
  margin: 0 0 15px 0;
}
</style>
