<template>
 <div style="width: 100%;">
  <div class="box" v-for="(item,index) in list" :key="index">
   <div class="header-box">
    <div class="img">
     <el-avatar
      :size="number"
      src="https://assets.pokemon.com/assets/cms2/img/pokedex/full/110.png">
       Avarta
     </el-avatar>
    </div>
    <span class="name">User</span>
    <div class="share"> <i class="el-icon-delete" @click="dele(index)"></i></div>
   </div>
   <div class="messageBox">{{item.message}}</div>
  </div>
   <el-button @click="drawer = true" type="primary" style="margin-left: 90%; margin-bottom: 18px;border-radius: 5px;border:.5px solid rgba(255,255,255,0.78); background-color: #523e7a;">
   Comments
   </el-button>
<el-drawer
:modal="false"
style="width: 1200px; margin: 0 auto;"
class="aaaaaaaaaaaaaaaaa"
  :visible.sync="drawer"
  :direction="direction"
  :show-close="false"
  :with-header="false"
 >
  <div class="addList">
    <div>
        <el-input class="textarea" type="textarea"
  :rows="2"
  placeholder="Please text here..."
  v-model="textarea">
</el-input>
    </div>
    <el-button round class="btnOk" type="success" @click="btnok">Confirm</el-button>
    <el-button round style=" margin-right:40px" class="btnOk" type="warning" @click="handleClose">Cancel</el-button>
  </div>
</el-drawer>

 </div>
</template>

<script>
export default {
  data () {
    return {
      drawer: false,
      direction: 'btt',
      textarea: '',
      number: 70,
      list: [{
        message: 'Very Good'
      },
      {

        message: 'This game is interesting'
      },
      {

        message: 'Good'
      },
      {

        message: 'Awesome!'
      }
      ]
    }
  },
  methods: {
    handleClose () {
      this.drawer = false
    },
    btnok () {
      this.list.unshift({
        message: this.textarea
      })
      this.drawer = false
      this.textarea = ''
    },
    dele (item) {
      this.list.splice(item, 1)
    }

  }
}
</script>

<style scoped>
.box {
  margin: 10px;
  padding:  10px;
  border: 2px solid #523e7a;
  border-radius: 16px;
  backdrop-filter: blur(10px);
  color: #ffffff;
}
.img{
    display: inline-block;
}
.header-box {
  width: 90%;
 height: 100px;
}
.name{
    margin-left: 10px;
}
.share{
    float: right;
    margin-right: 0px;
  margin-top: 10px;
  /*right: 0;*/
    font-size: 20px;
}
.messageBox{
    background: rgba(184, 158, 236, 0.7);
    height: 50px;
    padding: 10px;
    border-radius: 10px;
}
.addList{
padding: 10px;
    width: 100%;

}
.btnOk{
    float: right;
    margin-top: 20px;
    margin-right:20px
}
::v-deep .aaaaaaaaaaaaaaaaa .btt{
    height: 180px !important;
    border: 1px solid grey;
    border-radius: 12px 12px 0 0;
}
::v-deep  .el-textarea__inner{
background-color: white;
  height: 100px;
  max-height: 100px;
  min-height: 100px;
}
</style>
