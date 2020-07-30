<template>
  <div class="wyx-user">
        <div class="wyx-head">
            <daohang></daohang>
        </div>
        <div class="wyx-inp">
            <el-input v-model="input" placeholder="请输入内容">
            </el-input>
            <el-button type="primary" icon="el-icon-search"  @click="search"></el-button>
<el-button type="primary" icon="el-icon-search" @click="add">添加用户</el-button>
        </div>
        <div class="wyx-table">
            <table>
                <tr>
                    <th>
                        #
                    </th>
                    <th>学员名称</th>
                    <th>手机号</th>
                    <th>状态</th>
                    <th>创建时间</th>
                    <th>操作</th>
                </tr>
                <tr v-for="(item,index) in list" :key="index">
                    <td>
                        {{ index + 1 }}
                    </td>
                    <td>
                        <!-- <img width="20" :src="item.avatar" alt=""> -->
                        {{ item.role_name }}
                    </td>
                    <td>
                        {{ item.mobile }}
                    </td>
                    <td>
                        {{ item.mg_state == false?'启用':'禁用' }}
                    </td>
                    <td>
                        {{ date }}
                    </td>
                    <td>
                        <el-button type="primary" @click="bianji(item)" icon="el-icon-edit" circle></el-button>
                         <el-button type="danger" @click="del(index)" icon="el-icon-delete" circle></el-button>
                          <el-button type="warning" icon="el-icon-star-off" circle></el-button>
                    </td>
                </tr>
            </table>
            <div class="abb1" v-if="acd">
                    姓名：<input type="text" v-model="name"><br>
                    手机号：<input type="text" v-model="shouji"><br>
                    状态：<input type="text" v-model="zhuangtai">
                    <button @click="que">确认</button>
            </div>
            
            <el-pagination
                @current-change="change"
                background
                layout="prev, pager, next"
                :total="50">
            </el-pagination>
        </div>
  </div>
</template>

<script>
import daohang from "@/components/daihang"
export default {
  name: '',
  data() { 
    return {
        arr:[],
        list:[],
        input:"",
        flag:false,
        acd:false,
        date:new Date().toLocaleString(),
        name:'',
        shouji:'',
        zhuangtai:'',
        ming:''
    }
  },
  props: [

  ],
  components:{
    daohang
  },
  mounted() {
    this.$axios.get("/static/list.json").then((res)=>{
                this.arr = res.data.data.users
                this.list = this.arr
                console.log(this.list)
    })
  },
  methods:{
        change(){
            this.$axios.get("/static/list.json").then((res)=>{
                this.list = res.data.splice(0,5)
            })
        },
        search(){
            if(this.input==""){
                alert("输入框不能为空")
            }else{
                if(this.input == ""){
                    return false
                }else{
                    this.list = this.arr.filter((item,index)=>{
                        return item.role_name.includes(this.input)
                    })
                }
            }
        },
        bianji(item){
            this.$alert(`用户名:<input v-model="${this.ming}" type="text"/><br>手机号:<input v-modle="${this.ming}" type="text"/>`, '编辑用户', {
                dangerouslyUseHTMLString: true,
                showCancelButton:true,
                
            });
            this.ming=item.role_name
        },
        del(index){
            this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).then(() => {
            this.list.splice(index,1)
          this.$message({
            type: 'success',
            message: '删除成功!'
          });
        }).catch(() => {
          this.$message({
            type: 'info',
            message: '已取消删除'
          });          
        });
        },
        add(){
            this.acd=!this.acd
        },
        que(){
   if(this.name==""||this.shouji==""||this.zhuangtai==""){
                alert('没有可添加的东西')
                return false
            }
            for(var i in this.arr){
                if(this.arr[i].role_name==this.name){
                    alert("重复")
                    return false
                }
            }
            var obj={role_name:this.name,mobile:this.shouji,mg_state:this.zhuangtai}
            this.arr.push(obj)
            this.mobile=this.name=this.zhuangtai=""
            alert('添加成功')
            this.acd=!this.acd
        },
        aaa(){
            this.value = ""
            this.input = ""
            this.tell = ""
            this.$axios.get("/static/list.json").then((res)=>{
                this.arr = res.data
                this.list = this.arr
            })
        }
  },
 }
</script>

<style scoped>
.abb1{
    width: 300px;
    height: 200px;
    background: skyblue;
    position: absolute;
    top: 100px;
    left: 500px;
}
.wyx-user{
    width: 100%;
    height: 100%;
}
.wyx-head{
    margin-top:5px; 
    width: 100%;
    height: 30px;
    border: 1px solid black;
    line-height: 30px;
    margin-top: 10px;
    padding-top: 10px;
    padding-left:8px; 
    border-radius:10px; 
}
.wyx-head>span{
    margin-left: 30px;
}

.wyx-inp{
    width: 100%;
    height: 50px;
    display: flex;
}
.wyx-table>table{
    border: 2px solid blue;
    width: 1000px;
    text-align: center;
}
tr{
    border: 1px solid red;
}
</style>