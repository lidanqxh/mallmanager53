<template>
  <div class="login_warp">
    <el-form
      label-position="top"
      label-width="80px"
      class="login_form">
      <h2>用户登录</h2>
      <el-form-item label="用户名" prop="username">
        <el-input v-model="loginForm.username"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input v-model="loginForm.password"></el-input>
      </el-form-item>
      <el-button
        type="primary"
        class="login_btn"
        @click="handleLogin">登录
      </el-button>
    </el-form>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        loginForm: {
          username: 'admin',
          password: '123456'
        }
      }
    },
    methods: {
        async handleLogin() {
            const res = await this.$http.post('login', this.loginForm);
            const {
              data,
              meta: {msg, status}
            } = res.data;

            if (status === 200) {
              localStorage.setItem('token',data.token);
              this.$message.success(msg);
              this.$router.push({name: 'home'});
            } else {
              this.$message.warning(msg);
              this.$router.push({name: 'login'});
            }
        }
    }
  }
</script>
<style>
  .login_warp {
    height: 100%;
    background-color: #324152;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .login_warp .login_form {
    width: 400px;
    background-color: #fff;
    border-radius: 5px;
    padding: 30px;
  }

  .login_warp .login_btn {
    width: 100%;
  }
</style>
