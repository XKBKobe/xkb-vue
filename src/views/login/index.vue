<template>
  <div style="font-size: 40px;">
    <!--ref-->
    <el-form class="card-box login-form" name="loginForm" ref="loginForm" :rules="rules" :model="loginForm" autoComplete="on"
             label-position="left">
      <h2 class="title">元宝铺子 数据中心</h2>
      <el-card class="box-card">
        <div class="loginHeader">登录元宝铺数据中心</div>
        <div class="loginBody">
          <el-form-item label="用户名" prop="username">
            <el-input class="inputStyle" name="username" type="text" v-model="loginForm.username" placeholder="请输入你的用户名" @keyup.enter.native="handleLogin"></el-input>
          </el-form-item>
          <el-form-item label="密码" prop="password">
            <el-input class="inputStyle" name="password" type="password" v-model="loginForm.password" placeholder="请输入密码" @keyup.enter.native="handleLogin"></el-input>
          </el-form-item>
          <el-button type="primary" class="loginBtn" @click.native.prevent="handleLogin">登 录</el-button>
        </div>
      </el-card>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'login',
  data () {
    const validateAccount = (rule, value, callback) => {
      if (!value.trim()) {
        callback(new Error('请输入用户名'))
      } else {
        callback()
      }
    }
    const validatePwd = (rule, value, callback) => {
      if (!value) {
        callback(new Error('请输入密码'))
      } else {
        callback()
      }
    }
    return {
      loginForm: {
        username: '',
        password: ''
      },
      rules: {
        username: [{ required: true, trigger: 'blur', validator: validateAccount }],
        password: [{ required: true, trigger: 'blur', validator: validatePwd }]
      }
    }
  },
  methods: {
    handleLogin () {
      this.$message.warning('当前账户无可用权限')
      console.log('登录成功')
    }
  }
}
</script>
