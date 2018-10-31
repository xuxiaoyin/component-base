<template>
	<div>
		<v-header :msg="msg" :getData="getData" :home='this'></v-header>
		<button @click="getData">点击更新数据</button>
		<ul>
			<li v-for="item in list">{{item.TITLE}}</li>
		</ul>
		<br />
		<br />
		<br />
		<hr />
		<br />
		<br />
		<br />
		<button @click="emitNews()">非父子组件Home</button>
		<div>{{info}}</div>
		
	</div>
</template>

<script>
	import Header from './Header.vue'
	import VueEvent from '../model/VueEvent.js'
	export default{
		data(){
			return{
				list:[],
				index:1,
				totalPage:'',
				msg:'我是Home组件',
				info:'Home组件的值'
			}
		},
		components:{
			'v-header':Header
		},
		methods:{
			getData(){
				this.$http.jsonp('http://www.gd-info.gov.cn/ApiFindToArticleJsonp.action?',{
					params:{index:this.index,siteid:'ccq',topicid:'x1111',size:20},
					callback:'jsonData24'
					
				}).then(res=>{	
					console.log(res)
					this.list=res.body.data.list;
					this.totalPage=res.body.data.totalPage
					if(this.index<this.totalPage){
						this.index++;
					}else{
						this.index=this.totalPage;
						alert('已经是最后一页了')
					}
					console.log(this.list)
				},err=>{console.log(err)})
			},
			emitNews(){
				VueEvent.$emit('to-news',this.info);
			}
		},
		mounted(){
			this.getData();
			VueEvent.$on('to-home',data=>{
				this.info=data;
			})
		}
	}
</script>

<style>
</style>