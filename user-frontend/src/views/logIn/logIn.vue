<template>
  <div class="container">
    <div style="width: 50%; display: flex; background-color: white">
      <div style="width: 50%; border-radius: 10px">
        <img
          src="../../assets/image/b4.png"
          width="100%"
          height="100%"
          style="overflow: hidden"
        />
      </div>

      <div
        style="
          flex: 1;
          width: 50%;
          padding: 40px;
          display: flex;
          flex-direction: column;
          justify-content: center;
        "
      >
        <div
          style="
            text-align: center;
            font-size: 28px;
            font-weight: bold;
            margin-bottom: 50px;
            color: #258611;
          "
        >
          旅游信息推荐系统
        </div>
        <el-form :model="form" :rules="rules" ref="formRef">
          <el-form-item prop="username" style="margin-bottom: 40px">
            <el-input
              prefix-icon="el-icon-user"
              v-model="loginAccount"
              placeholder="请输入登录账号"
            ></el-input>
          </el-form-item>
          <el-form-item prop="password" style="margin-bottom: 40px">
            <el-input
              prefix-icon="el-icon-star-off"
              type="password"
              v-model="password"
              placeholder="请输入用户密码"
            ></el-input>
          </el-form-item>

          <div style="display: flex">
            <el-button
              style="
                width: 100%;
                background-color: #3c81ff;
                color: white;
                flex: 4;
              "
              @click="login"
              >登 录</el-button
            >
            <el-button
              style="
                width: 100%;
                background-color: #16ad05;
                color: white;
                flex: 4;
              "
              @click="toRegister"
              >注册</el-button
            >
            <el-button
              style="
                width: 100%;
                background-color: #de8602;
                color: white;
                flex: 4;
              "
              @click="toForget"
              >忘记密码</el-button
            >
          </div>
        </el-form>
      </div>
    </div>

    <el-dialog
      title="注册"
      :visible.sync="dialogVisible"
      width="30%"
      :before-close="handleClose"
    >
      <div style="display: flex; flex-direction: column; gap: 20px">
        <el-input
          prefix-icon="el-icon-user"
          v-model="loginAccount"
          placeholder="请输入登录账号"
        ></el-input>
        <el-input
          prefix-icon="el-icon-star-off"
          type="password"
          v-model="password"
          placeholder="请输入用户密码"
        ></el-input>
        <el-input
          prefix-icon="el-icon-s-platform"
          v-model="userName"
          placeholder="请输入用户名"
        ></el-input>
        <el-input
          prefix-icon="el-icon-s-order"
          v-model="email"
          placeholder="请输入邮箱"
        ></el-input>
        <el-input
          prefix-icon="el-icon-s-ticket"
          v-model="tel"
          placeholder="请输入联系电话"
        ></el-input>
      </div>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="saveUser">提 交</el-button>
      </span>
    </el-dialog>

    <!--    忘记密码-->
    <el-dialog
      title="找回密码"
      :visible.sync="dialogVisible1"
      width="30%"
      :before-close="handleClose"
    >
      <div style="display: flex; flex-direction: column; gap: 20px">
        <el-input
          prefix-icon="el-icon-user"
          v-model="loginAccount"
          placeholder="请输入登录账号"
        ></el-input>
        <el-input
          prefix-icon="el-icon-star-off"
          type="password"
          v-model="password"
          placeholder="请输入新密码"
        ></el-input>
        <el-input
          prefix-icon="el-icon-s-order"
          v-model="email"
          placeholder="请输入邮箱"
        ></el-input>
        <el-input
          prefix-icon="el-icon-s-ticket"
          v-model="code"
          placeholder="请输入验证码"
        ></el-input>
        <el-button
          @click="getEmailReg"
          style="color: #fff; text-align: center; background-color: #3e78f3"
        >
          获取验证码
        </el-button>
      </div>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible1 = false">取 消</el-button>
        <el-button type="primary" @click="forgetPassword">提 交</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
import {
  login,
  getUser,
  saveUser,
  forgetPassword,
  getEmailReg,
} from '../../api/api'
export default {
  data() {
    return {
      loginAccount: '',
      password: '',
      userName: '',
      type: '1',
      email: '',
      tel: '',
      dialogVisible: false,
      dialogVisible1: false,
      code: '',
    }
  },
  methods: {
    forgetPassword() {
      if (!this.loginAccount) {
        this.$message({
          message: '请输入登录账号',
          type: 'warning',
        })
        return
      }
      if (!this.password) {
        this.$message({
          message: '请输入密码',
          type: 'warning',
        })
        return
      }
      if (!this.code) {
        this.$message({
          message: '请输入用户名',
          type: 'warning',
        })
        return
      }
      if (!this.email) {
        this.$message({
          message: '请输入邮箱',
          type: 'warning',
        })
        return
      }
      var regex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/ // 邮箱正则表达式
      if (!regex.test(this.email)) {
        this.$message({
          message: '请输入正确的邮箱格式',
          type: 'warning',
        })
        return
      }
      var param = {
        loginAccount: this.loginAccount,
        password: this.password,
        email: this.email,
        code: this.code,
      }
      forgetPassword(param).then((res) => {
        if (res.code == 1000) {
          this.dialogVisible1 = false
          this.$message({
            message: '密码修改成功',
            type: 'success',
          })
          var that = this
          setTimeout(function () {
            that.$router.push('/login')
          }, 500)
        } else {
          this.$message({
            message: res.message,
            type: 'warning',
          })
        }
      })
    },
    getEmailReg() {
      if (!this.email) {
        this.$message({
          message: '请输入邮箱',
          type: 'warning',
        })
        return
      }
      var regex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/ // 邮箱正则表达式
      if (!regex.test(this.email)) {
        this.$message({
          message: '请输入正确的邮箱格式',
          type: 'warning',
        })
        return
      }
      getEmailReg({ email: this.email }).then((res) => {
        if (res.code == 100) {
          this.$message({
            message: '验证码已发送',
            type: 'success',
          })
        } else {
          this.$message({
            message: res.message,
            type: 'warning',
          })
        }
      })
    },
    handleClose(done) {
      this.$confirm('确认关闭？')
        .then((_) => {
          done()
        })
        .catch((_) => {})
    },
    toLogin() {
      this.dialogVisible = false
    },
    saveUser() {
      if (!this.loginAccount) {
        this.$message({
          message: '请输入登录账号',
          type: 'warning',
        })
        return
      }
      if (!this.password) {
        this.$message({
          message: '请输入密码',
          type: 'warning',
        })
        return
      }
      if (!this.userName) {
        this.$message({
          message: '请输入用户名',
          type: 'warning',
        })
        return
      }
      if (!this.email) {
        this.$message({
          message: '请输入邮箱',
          type: 'warning',
        })
        return
      }
      var regex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/ // 邮箱正则表达式
      if (!regex.test(this.email)) {
        this.$message({
          message: '请输入正确的邮箱格式',
          type: 'warning',
        })
        return
      }
      if (!this.tel) {
        this.$message({
          message: '请输入联系方式',
          type: 'warning',
        })
        return
      }
      var param = {
        loginAccount: this.loginAccount,
        password: this.password,
        userName: this.userName,
        email: this.email,
        tel: this.tel,
        userType: 1,
      }
      saveUser(param).then((res) => {
        if (res.code == 1000) {
          if (this.type == 2) {
            this.$message({
              message: '正在审核，审核完成后会将结果发送到您的邮箱，请注意查收',
              type: 'success',
            })
          } else {
            this.dialogVisible = false
            this.$message({
              message: '注册成功',
              type: 'success',
            })
          }
          var that = this
          setTimeout(function () {
            that.$router.push('/login')
          }, 500)
        } else {
          this.$message({
            message: res.message,
            type: 'warning',
          })
        }
      })
    },
    toRegister() {
      this.dialogVisible = true

      // this.$router.push("/register")
    },
    toForget() {
      this.dialogVisible1 = true
    },
    login() {
      if (!this.loginAccount) {
        this.$message({
          message: '请输入用户名',
          type: 'warning',
        })
        return
      }
      if (!this.password) {
        this.$message({
          message: '请输入密码',
          type: 'warning',
        })
        return
      }
      var params = {
        loginAccount: this.loginAccount,
        password: this.password,
      }
      login(params).then((res) => {
        if (res.code == 1000) {
          this.$message({
            message: '登陆成功',
            type: 'success',
          })
          var that = this
          var token = res.data.token
          window.localStorage.setItem('user_token', token)
          this.getUserInfo()
          setTimeout(function () {
            that.$router.push('/')
          }, 500)
        } else {
          this.$message.error(res.message)
        }
      })
    },
    getUserInfo() {
      getUser().then((res) => {
        if (res.code == 1000) {
          window.localStorage.setItem('user_info', JSON.stringify(res.data))
        }
      })
    },
  },
  created() {},
  mounted() {},
}
</script>

<style scoped>
.container {
  height: 100vh;
  overflow: hidden;
  background-color: #409eff;
  background-size: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #666;
}
/*@import url('../../assets/css/login.css');*/
</style>
