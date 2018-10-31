<template>
	<div>
		<v-header :msg="msg" :getData="getData" :home='this'></v-header>
		<button @click="getData">点击更新数据</button>
		<ul>
			<li v-for="item in list">{{item.TITLE}}</li>
		</ul>
	</div>
</template>

<script>
	import Header from './Header.vue'
	export default{
		data(){
			return{
				list:[],
				index:1,
				totalPage:'',
				msg:'我是Home组件'
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
			}
		},
		mounted(){
			this.getData();
		}
	}
</script>

<style>
</style>