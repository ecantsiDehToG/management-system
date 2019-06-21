<template>
  <div class="login">
    <div class="content">
      <h2>用户登录</h2>
      <el-form :rules='rules'
               status-icon
               label-position='top'
               ref='ruleform'
               label-width="100px"
               class="demo-ruleForm"
               :model="userobj">
        <el-form-item prop="username"
                      label="用户名:">
          <el-input type="text"
                    autocomplete="off"
                    v-model="userobj.username"></el-input>
        </el-form-item>
        <el-form-item prop="password"
                      label="密码:">
          <el-input type="password"
                    autocomplete="off"
                    v-model='userobj.password'></el-input>
        </el-form-item>

        <el-form-item>
          <el-button class="btn"
                     type="primary"
                     @click.prevent='login'>登录</el-button>

        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  data () {
    return {
      userobj: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    login () {
      //validate是h5新增的表单验证的方法,老师没说怎么用,那反正就记住这样用,不会就去elementui中抄
      this.$refs['ruleform'].validate((valid) => {
        //vue中通过$refs来获取dom元素,首先在该元素身上绑定一个自定义属性ref="属性名",然后在js中通过this.$refs.属性名 来获取这个dom元素
        // this.$refs[字符串格式的已经绑定的属性名] 这种方式也能获取到这个dom元素,然后this.$refs.属性名 也可以获取到
        if (valid) {
          //解构赋值
          const { username, password } = this.userobj
          this.$http({
            method: 'POST',
            url: 'http://localhost:8888/api/private/v1/login',
            data: { username, password }
          }).then(res => {
            // console.log(res);
            // 结构赋值
            let { data, meta } = res.data
            if (meta.status == 200) {
              //将token保存到localstorage中
              window.localStorage.setItem('token', data.token)
              this.$router.push('/')
              this.$message({
                message: meta.msg,
                type: 'success'
              })
            } else {
              this.$message.error(meta.msg);
            }

          }).catch(err => {
            console.log(err);

          })
        } else {
          console.log('请输入用户名和密码!!');
          return false;
        }
      });



    }
  },
  components: {

  }
}
</script>

<style scoped>
.login {
  background-color: #324152;
  width: 100%;
  height: 100%;
  position: relative;
}
.content {
  width: 580px;
  height: 440px;
  background-color: #fff;
  border-radius: 5px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 40px;
  box-sizing: border-box;
}
.btn {
  width: 100%;
}
</style>
