<template>
  <div class="bgd">
 <div class="home">
  <div class="prompt" style="margin-left: 15px">  <h3>Hi, Friend.</h3>   <h3 style="float:right;margin-right: 12px">My Account</h3></div>
  <el-tabs class="eltabs" v-model="activeName" @tab-click="handleClick">
   <el-tab-pane label="Home" name="first">
    <div style="width: 1300px; margin: 0 auto">
     <div class="block">
      <el-carousel height="600px" style="width:100%">
       <el-carousel-item v-for="(item,index) in list" :key="index">
       <img style="width:100%" :src="item.src" alt="">
       </el-carousel-item>
      </el-carousel>
     </div>
    </div>
   </el-tab-pane>
   <el-tab-pane label="Community" name="second">
    <div style="width: 1200px; margin: 0 auto">
     <CommunityVue />
    </div>
   </el-tab-pane>
   <el-tab-pane label="Contact" name="third">
    <div style="width: 1200px; margin: 0 auto">
     <ContactVue />
    </div>
   </el-tab-pane>
   <el-tab-pane label="My profile" name="fourth">
   <myprofile />
   </el-tab-pane>
   <el-tab-pane label="MyGameRank" name="Game" style="color: white; background-color: black"> Game Rank</el-tab-pane>
  </el-tabs>
 </div>
    <el-button @click="drawer = true" type="primary" style="margin-left: 50%;border-radius: 5px;border:.5px solid rgba(255,255,255,0.78); background-color: #523e7a;">
      Start Game
    </el-button>
  </div>
</template>
<script>
import myprofile from '@/components/myprofile'
import ContactVue from '@/components/Contact.vue'
import CommunityVue from '@/components/Community.vue'

export default {
  components: {
    ContactVue,
    CommunityVue,
    myprofile

  },
  data () {
    return {
      activeName: 'third',
      list: [{ src: '@/assets/banner1.jpg' }, { src: '@/assets/banner2.jpg' }, { src: '@/assets/banner3.jpg' }]
    }
  },
  methods: {
    handleClick (tab, event) {
      console.log(tab, event)
    }
  }
}
</script>

<style scoped>
*{
  font-family: sans-serif;
}
.bgd{
  height: 790px;
  background:url(../assets/bcg1.jpg) no-repeat;
  background-size:100% 100%;
  background-attachment:fixed;
}
.home {
 width: 100%;
 margin: 0 auto;
  background:url(../assets/bcg1.jpg) no-repeat;
  background-size:100% 100%;
  background-attachment:fixed;
}
.el-carousel__item h3 {
 color: #475669;
 font-size: 14px;
 opacity: 0.75;
 line-height: 150px;
 margin: 0;
}
.el-carousel__item:nth-child(2n) {
 background:url(../assets/banner1.jpg) no-repeat;
  background-size:100% 100%;
  background-attachment:fixed;
}
.el-carousel__item:nth-child(2n + 1) {
 background:url(../assets/banner2.jpg) no-repeat;
  background-size:100% 100%;
  background-attachment:fixed;
}
.el-carousel__item:nth-child(3) {
 background:url(../assets/banner3.jpg) no-repeat;
  background-size:100% 100%;
  background-attachment:fixed;
}

::v-deep .eltabs .el-tabs__header{
  width: 98%;
  border-radius: 10px;
  background-color: rgb(82, 62, 122);
  height: 70px;
  margin: 0 auto;
  margin-top: 2px;
  margin-bottom: 10px;

}
::v-deep .el-tabs__nav-wrap::after{
  display: none;
}
::v-deep .el-tabs__item.is-active{
  text-align: center;
  font-size: 21px;
  width: 200px;
  color: #fff;
  line-height: 70px;
  height: 70px;
}
::v-deep .el-tabs__item{
  color: rgb(255, 186, 186);
  text-align: center;
  font-size: 21px;
  width: 200px;
  line-height: 70px;
  height: 70px;
}
::v-deep .el-tabs__active-bar{
  display: none;
}
.prompt h3{
  color: rgb(255, 255, 255);
   display: inline-block;
  border-radius: 1px;
  background-color: black;
}
</style>
