<template>
	<div class="lunbo">
      <ul class="headpicul" v-if="lang == 'zh'">
        <li v-for='(image,index) in img' :key='index' v-show='index==mark'>
          <img style="width:95%;border-radius: 7px;"  :src='image' @click="openDapp(index)"/>
        </li>
      </ul>
			<ul class="headpicul" v-if="lang != 'zh'">
        <li v-for='(image,index) in imgen' :key='index' v-show='index==mark'>
          <img style="width:95%;border-radius: 7px;"  :src='image' @click="openDapp(index)"/>
        </li>
      </ul>
    </div>
</template>

<script>
	import Links from '../../common/links'
	import trans from '../../common/utils/trans'
	export default {
	  name: 'Head',
	  components: {},
	  data () {
	    return {
	    	mark:0,
				lang: '',
      	img:[
      		'static/images/trade_en.png',
      		'static/images/eash2_en.png',
      		'static/images/etz_cn.png',
      		'static/images/zerodice.png',
      		'static/images/popular_bar.png'
				],
				imgen:[
      		'static/images/trade_en.png',
      		'static/images/eash2_en.png',
      		'static/images/etz_cn.png',
      		'static/images/zerodice.png',
      		'static/images/popular_bar.png'
				]
	    };
	  },
	  mounted() {
	  	this.init()
	  },
	  updated:function(){
	  },
	  methods: {
	  	init:function(){
				let that = this;
				that.lang = that.$i18n.locale;
	  		window.setInterval(()=>{
	        this.autoPlay()
	      },3000);
	  	},
	  	autoPlay() {
		      this.mark++
		        if(this.mark === 5){
		          this.mark = 0 
		          return;
		        }
		  },
		 openDapp:function(index){
		 	console.log(index)
		 	if(index==0){
		 		trans.$emit("tipsemit",{"name":"Biduoduo","link":Links.url.biduoduo,"state":0});
		 	}else if(index==1){
		 		trans.$emit("tipsemit",{"name":"Eash","link":Links.url.eash,"state":0});
		 	}else if(index==2) {
		 		trans.$emit("tipsemit",{"name":"Biduoduo","link":Links.url.biduoduo,"state":0});
		 	}else if(index==3){
		 		trans.$emit("tipsemit",{"name":"Zerodicelogo","link":Links.url.biduoduo,"state":0});
		 	}else if(index==4){
		 		trans.$emit("tipsemit",{"name":"NumberOne","link":Links.url.masternode_plan,"state":0});
		 	}
		 	
		 },
		 linkx:function(name,link){
		 	  let dname = window.localStorage.getItem(name);
		      if(dname){
		        window.open(link,'_self')
		      }else{
		        trans.$emit("tipsemit",{"name":name,"link":link});
		      }
		 }
	  }
	}

</script>

<style scoped>
.lunbo{
	margin-top: 60px;
}
.headpicul{
  list-style: none;
  padding:0;
  margin:0;
}
</style>