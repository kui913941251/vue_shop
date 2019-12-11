<template>
  <div id="login">
    <!--登录窗口-->
    <div class="login-box">
      <!--头像区域-->
      <div class="login-portrait">
        <img src="../assets/img/logo.png" alt="">
      </div>
      <el-form class="login-form" :model="form" :rules="rules" ref="formName">
        <!--用户名-->
        <el-form-item class="login-username" prop="username">
          <el-input prefix-icon="el-icon-user-solid" placeholder="用户名"  v-model="form.username"></el-input>
        </el-form-item>
        <!--密码-->
        <el-form-item class="login-password" prop="password">
          <el-input prefix-icon="el-icon-key" placeholder="密码"  v-model="form.password"
          type="password"></el-input>
        </el-form-item>
        <el-row class="login-btns">
          <el-button type="primary" @click="onSubmit">登录</el-button>
          <el-button type="info" @click="formNameRef">重置</el-button>
        </el-row>
      </el-form>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Login",
    data() {
      return {
        form: {
          username: '',
          password: ""
        },
        rules: {
          username: [
            {required: true, message: '请输入用户名', trigger: 'blur'},
            {min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur'}
          ],
          password: [
            { required: true, message: '请输入密码', trigger: 'blur' },
            { min: 6, max: 18, message: '长度在 6 到 18 个字符', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      onSubmit() {
        this.$refs.formName.validate().then(res => {
          console.log(res)
        }).catch(err => {
          console.log(err)
        })
      },
      formNameRef() {
        this.$refs.formName.resetFields()
      }
    }
  }
</script>

<style scoped>
  #login{
    height: 100%;
    background-color: #636e72;
  }
  .login-box{
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50% , -50%);
    width: 500px;
    height: 300px;
    background-color: #fff;
    border-radius: 10px;
  }
  .login-portrait{
    position: absolute;
    left: 50%;
    transform: translate(-50% , -50%);
    width: 130px;
    border-radius: 50%;
    padding: 10px;
    background-color: #fff;
  }
  .login-portrait img{
    width: 100%;
    border-radius: 50%;
    background-color: #dfe6e9;
  }
  .login-form{
    position: absolute;
    top: 90px;
    left: 50%;
    transform: translate(-50% , 0);
    width: 60%;
  }
  .login-btns{
    display: flex;
    justify-content: flex-end;
  }
</style>