<template>
  <div id="app">
        <Loading v-if="Loading"></Loading>
        <router-view></router-view>
  </div>
</template>
<script>
export default {
    name: "app",
    data(){
        return {
            
        }
    },
    components:{
        
    },
    methods:{

    },
    mounted(){
       
    },
    created(){

    },
    computed:{
        Loading(){
            return this.$store.state.Loading
        }
    }
}
</script>
<style>
*{
    padding: 0;
    margin: 0;
    list-style: none;
}
html,body,#app{
    height: 100%;
}

</style>