<template>
   <div class="app-login">
      <form>
        <p class="yh">账号</p>
  <input type="text" name="uname" v-model="uname" placeholder="请输入账号" class="an"/>
      <br/>
      <p class="yh">密码</p>
  <input type="password" name="upwd" v-model="upwd" placeholder="请输入密码" class="an"/>
      <br />
  <input type="button" value="登录" @click="btnLogin" class="bt"/>
      </form>
   </div>
</template>
<script>
  //1:引入mint-ui Toast 局部使用
  import {Toast} from "mint-ui"
  export default {
    data(){
      return {
        uname:"",
        upwd:""
      }
    },
    methods:{
      btnLogin(){
        //console.log(123);
        //1:获取用户输入用户名和密码
        var u = this.uname;
        var p = this.upwd;
        //console.log(u+":"+p);
        //2:创建正则表达式验证用户名和密码格式是//否正确
        var reg = /^[a-z0-9_]{3,8}$/i;
        if(!reg.test(u)){
          //提示信息不是
          Toast("用户名格式不正确,请检查");
          return;
        }
        if(!reg.test(p)){
          Toast("密码格式不正确，请检查");
          return;
        }
        //3:发送ajax
        //console.log(3);
        var url = "http://127.0.0.1:3000";
        url+="/login?uname="+u+"&upwd="+p;
        this.axios.get(url).then(result=>{
             //11:41
             if(result.data.code==1){
               Toast("登录成功");
               this.$router.push("Index")
             }else{
               Toast("用户名或密码有误")
             }
        });
        //4:获取服务器返回结果
        //5:提示用户 36  
      }
    }
  }
</script>
<style>
.yh{
    padding:0;
    margin-left:10px;
    margin-top:10px;
    font-size:12px;
    color:#3C2314;

}
.an{
    height:20px;
    font-size:12px;
}
.bt{
    width:100%;
    height:30px;
    
}
</style>