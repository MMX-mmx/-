<template>
  <div class="home">
        <div class="wyx-head"></div>
  <div style="display:flex">
          <div class="elc">
          <el-col :span="24">
    <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose"
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b">
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>用户管理</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="1-1" @click="userb()">用户列表</el-menu-item>
          <el-menu-item index="1-2" @click="userc()">切换测试</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
      <el-submenu index="2">
        <template slot="title">
          <i class="el-icon-menu"></i>
          <span>用户列表</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
      <el-submenu index="3">
        <template slot="title">
          <i class="el-icon-document"></i>
          <span>权限管理</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
      <el-submenu index="4">
        <template slot="title">
          <i class="el-icon-setting"></i>
          <span>商品管理</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
      <el-submenu index="5">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>订单管理</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
      <el-submenu index="6">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>数据统计</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
    </el-menu>
  </el-col>
  </div>
  <div>
          <User v-if="user1"></User>
          <aa v-if="user2"></aa>
  </div>
  </div>
  </div>
</template>
<script>
import User from "@/components/user"
import aa from './aa'
export default {
  name: '',
  data() { 
    return {
        index:0,
        user1:false,
        user2:false
    }
  },
  props: [
        
  ],
  components:{
        User,
        aa
  },
  mounted() {
        
  },
  methods:{

        handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      },
      userb(){
        this.user1=true
        this.user2=false
      },
      userc(){
        this.user1=false
        this.user2=true
      }

  },
 }
</script>

<style scoped>
.home{
        width: 100%;
        height: 92%;
}
.wyx-head{
        width: 100%;
        height: 80px;
        background:skyblue;
}
.elc{
        width: 500px;
        height: 100%;
}
.elc el-col{
        width: 100%;
        height: 100%;
}
.content{
        width: 100%;
        height: 100%;
        display: flex;
}
.left{
        width: 10%;
        height: 100%;
        text-align: center;
        border-right: 1px solid black;
}
.content>.left>ul{
        width: 100%;
        height: 100%;
}
.content>.left>ul>li{
        height: 50px;
        line-height: 50px;
}
.right{
        width: 100%;
        height: 100%;
}
.active{
    color:skyblue;
}
</style>