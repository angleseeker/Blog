<template>
    <div class="login-box">
    <form>
          <section class="input-box" id="account">
              
              <input id="AN" type="text"  @keyup.enter="add" name="AN" placeholder="用户名"
               autocomplete="on" v-model="formMess.username">
              <span id="namemsg"></span>
          </section>
          <section class="input-box" id="secrit">
              
              <input id="SC"  type="text"  @keyup.enter="add" name="SC" placeholder="密码"
               autocomplete="on" v-model="formMess.password">
              <span id="scmsg"></span>
          </section>
          <div  class="input-btn" @click="onSubmit()">
              登录
          </div>
    </form>
  </div>
</template>

<script>
import { request } from "../network/request";

export default {
  name: 'HomeView',
  components: {
    
  },
  data(){
    return {
      result:'',
      formMess:{
	    "username":"",
	    "password":"",
	}

    }
  },
  created(){
  },
  methods:{
    onSubmit() {
      let formData = new FormData();
      for(let key in this.formMess){
        formData.append(key,this.formMess[key]);
      }
     request({
      url: '/login',
      method:'post',
      data:formData
    }).then((res)=>{
            console.log(res);
        });
    }
  }
}
</script>

<style scoped>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;width: 100%;
  
}
.login-box{
  top: 200px;
  position: relative;
  margin:auto;
  width:600px;
  height: 400px;
  background-color: rgba(65, 62, 62, 0);
  border: 10px;
  /*padding: 20px 50px;*/
}
.login-box .input-box{
  width: 100%;
}
form{
  position: absolute;
  width: 100%;
  margin-top: 15%;
  text-align: center;
  
}
 span{
  color: white;
  font-size: 18px;
  margin-top: 20px;
}
 input{
  width: 250px;
  height: 40px;
  font-size: 16px;
  border: 0;
  padding: 10px;
  border-bottom: 1px solid white;
  background-color: #ffffff00;
  color: #fff;
  margin-top: 20px;
}
input:focus{
  outline: none;
}
.input-btn{
  margin-top: 25px;
  font-size: 14px;
  width: 145px;
  height: 40px;
  line-height: 40px;
  color: #fff;
  background: linear-gradient(120deg,#a6c0fe 0%,#f68084 100%);
  border-radius: 25px;
  cursor: pointer;
  margin: auto;
  margin-top: 40px;
}
</style>
