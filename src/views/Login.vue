<template>
 <div class="Login">
  <div class="title">
   <h1>Sign In</h1>
  </div>
  <div class="form">
   <el-form :rules="rules" class="formbox" ref="form" :model="form" label-width="80px">
    <el-form-item label="Account" prop="Account">
     <el-input class="input" v-model="form.Account"></el-input>
     <span style="font-size: 12px;color: green;">The length ranges from 6 to 15 characters</span>
    </el-form-item>
    <el-form-item label="Password" prop="Password">
     <el-input class="input" v-model="form.Password"></el-input>
    </el-form-item>
    <el-button style="margin-left: 190px;" class="btn"  round>Sign Up</el-button>
  <el-button class="btn" round @click="btnOK">Sign In</el-button>
   </el-form>
   <el-divider><p style="   font-weight: 500;">Sign In Withs</p></el-divider>
   <div class="icon">
     <ul>
      <li>
        <img src="@/assets/logos/facebook.png" alt="">
      </li>
      <li>
        <img src="@/assets/logos/github.png" alt="">
      </li>
      <li>
        <img src="@/assets/logos/instagram.png" alt="">
      </li>
      <li>
        <img src="@/assets/logos/twitter.png" alt="">
      </li>
     </ul>

   </div>
  </div>

 </div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        Account: '',
        Password: ''

      },
      rules: {
        Account: [
          { required: true, message: 'Please enter your account', trigger: 'blur' },
          { min: 6, max: 15, message: 'The length ranges from 6 to 15 characters', trigger: 'blur' }
        ],
        Password: [
          { required: true, message: 'Please enter your password', trigger: 'blur' },
          { min: 6, max: 15, message: 'The length ranges from 6 to 15 characters', trigger: 'blur' }
        ]

      }
    }
  },
  methods: {
    btnOK () {
      this.$refs.form.validate(isok => {
        if (isok) {
          this.$router.push('/Home')
        }
      })
    }
  }
}
</script>

<style scoped>
* {
 padding: 0;
 margin: 0;
 font-family: sans-serif;
 text-decoration: none;
 list-style: none;
}
.Login {
 background-position: center;
 background-image: linear-gradient(135deg, #fff5c3 10%, #9452a5 100%);
}
.title {
 width: 100%;
 height: 150px;
 /* background-color: pink; */
 line-height: 150px;
}
.title h1 {
 margin-left: 300px;
}
.form {
 height: 520px;
 width: 100%;
 background: #fff;
 padding-top: 50px;
 /* padding: 0px 200px 0px 200px */
}
.formbox{
    width: 500px;
    height: 240px;
    margin: 0 auto;
}
.btn{
    color: #fff;
width: 150px;
    background-color: rgb(115, 187, 115);
    border: 0;
}
/* .input{
    border: .8px solid rgb(86, 150, 86);
    border-radius: 12px;
} */
::v-deep .el-input__inner{
    border: .8px solid rgb(86, 150, 86);
    border-radius: 12px;
}
.icon{

    /* background: pink; */
    margin: 0 auto;
    width: 250px;
    height: 25px;
}
.icon ul li{
   display: inline-block;
  width: 25%;

}
.icon ul {
  display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    height: 100%;
    list-style: none;
}
.icon ul li img {
  height: 25px
}
</style>
