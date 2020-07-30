<template>
  <div>
    <div class="mmx-head">
    <el-breadcrumb separator="/">
        <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
        <el-breadcrumb-item><a href="/">用户管理</a></el-breadcrumb-item>
        <el-breadcrumb-item>用户列表</el-breadcrumb-item>
    </el-breadcrumb>
    </div>
  </div>
</template>

<script>
export default {
  name: '',
  data() { 
    return {

    }
  },
  props: [

  ],
  components:{
  },
  mounted() {

  },
  methods:{

  },
 }
</script>

<style scoped>
.mmx-head{
    margin-top:5px; 
    width: 800px;
    height: 30px;
    border: 1px solid black;
    line-height: 30px;
    margin-top: 10px;
    padding-top: 10px;
    padding-left:8px; 
    border-radius:10px; 
}
</style>