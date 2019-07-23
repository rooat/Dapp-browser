<template>
<div class=excelentdiv>
    <ul class="exelentdapp">
      <li class="titlename">{{$t("message.popular")}}</li>
      <li class="moreli" >&nbsp;</li>
    </ul>
  <div class="detaildapp">
      <img class="popularimg" @click="popular_master_btn" src="static/images/popular_img.png"/>
     <!--  <ul class="excellcontent">
        <li>{{$t("message.mall")}}</li>
        <li class="secondtitle">{{$t("message.mallcomment")}}</li>
      </ul> -->
    </div>
</div>
</template>

<script>
  import Links from '../../common/links'
  import trans from '../../common/utils/trans'
	export default{
	  name: 'MainScreen',
	  components:{

	  },
	  data () {
	    return {
        deving:String
	    }
	  },
	  mounted() {

	  },
	  methods: {
		     popular_master_btn:function(){
          let dname = window.localStorage.getItem("NumberOne");
          if(dname){
            window.open(Links.url.masternode_plan,'_self')
          }else{
            trans.$emit("tipsemit",{"name":"NumberOne","link":Links.url.masternode_plan,"state":0});
          }
        },
	  }
	}
</script>

<style>
.excelentdiv{
  margin-left: 20px;
  margin-right:20px;
  height: 300px;
}
.secondtitle{
	color:rgba(153,172,187,1);
	padding-top:10px;
	font-size: 20px;
}
.moreli{
  float:right;
}
.titlename{
  float:left;
  font-weight:bold;
}
.exelentdapp{
  clear:both;
  padding:0;
  list-style:none; 
  font-size: 33px;
  height: 20px;
}
.detaildapp{
  clear:both;
  padding-top:20px;
  height: 120px;
}
.popularimg{
  width: 100%
}

</style>