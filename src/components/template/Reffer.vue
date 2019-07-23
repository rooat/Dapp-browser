<template>
  <div>
	<table class="reffertable">
      <tr>
        <td><img class="refferpic" :src="zerodicelogo" @click="zerodicelogobtn"/></td>
        <td><img class="refferpic" :src="zerotrap" @click="zerotrapbtn"/></td>
        <td><img class="refferpic" :src="eash" @click="eashbtn"/></td>
        <td><img class="refferpic" :src="blockoptions" @click="blockoptionsbtn"/></td>
        
      </tr>
      <tr>
        <td @click="zerodicelogobtn">{{$t("message.zerodicelogo")}}</td>
        <td @click="zerotrapbtn">{{$t("message.zerotrap")}}</td>
        <td @click="eashbtn">{{$t("message.eash")}}</td>
        <td @click="blockoptionsbtn">{{$t("message.blockoptions")}}</td>
        
      </tr>
    </table>
    <div v-show="isshowtoast" class="isshowclass">
      <p>{{$t("message.updating")}}</p>
      <span class="closeclass" @click="closedivbtn">{{$t("message.close")}}</span>
    </div>
  </div>
</template>

<script>
import Links from '../../common/links'
import trans from '../../common/utils/trans'
export default {
  name: 'MainScreen',
  components:{
  },
  data () {
    return {
      zerotrap:'static/images/zerotrap.png',
      eash:'static/images/eash.png',
      blockoptions:'static/images/blockoptions.png',
      zerodicelogo:'static/images/zerodicelogox.png',
      isshowtoast:false
    }
  },
  mounted() {

  },
  methods: {
    eashbtn:function (event) {      
      let dname = window.localStorage.getItem("Eash");
      if(dname){
        window.open(Links.url.eash,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"Eash","link":Links.url.eash,"state":0});
      }
    },
    zerotrapbtn:function(event){
      let dname = window.localStorage.getItem("ZeroTrap");
      if(dname){
        window.open(Links.url.zerotrap,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"ZeroTrap","link":Links.url.zerotrap,"state":0});
      }
    },
    blockoptionsbtn:function(){
      
      let dname = window.localStorage.getItem("Blockoptions");
      if(dname){
        window.open(Links.url.blockoptions,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"Blockoptions","link":Links.url.blockoptions,"state":0});
      }
    },
    zerodicelogobtn:function(){
      let dname = window.localStorage.getItem("Zerodicelogo");
      if(dname){
        window.open(Links.url.zerodicelogo,'_self')
      }else{
        trans.$emit("tipsemit",{"name":"ZeroDice","link":Links.url.zerodicelogo,"state":0});
      }
    },
    closedivbtn:function(){
      this.isshowtoast=false
    }
  }
}
</script>

<style>
.isshowclass{
  background-color: #f1f4f5;
  position: absolute;
  top:30%;
  width: 50%;
  left:25%;
  height: 180px;
  border-radius: 10px;
  line-height: 60px;
}
.reffertable{
  width: 100%;
  margin:30px 0 50px 0;
  font-size: 28px;
  background: #fdfbfb;
  border-radius: 10px;
}
.reffertable tr td{
  width:25%;
}
.reffertable img{
  width:85%;
}

.reffertable p{
  margin:0;
  padding:0;
}
.closeclass{
  background-color: #f1e0e0
}

</style>