<template>
	<div>
		<br />
		<br />
		<br />
		<hr />
		<br />
		<br />
		<br />
		<button @click="emitHome">非父子组件News</button>
		<div>{{info}}</div>
		
		<h1>{{msg}}</h1>
		<button @click="change()">改变父组件</button>
		<v-foot ref='footer'></v-foot>
	</div>
</template>

<script>
	import Footer from './Footer.vue'
	import VueEvent from '../model/VueEvent.js'
	export default{
		data(){
			return{
				msg:'父组件',
				msg1:'我是父组件里面的值',
				info:'News组件的值',
				info1:'News组件的值'
			}
		},
		components:{
			'v-foot':Footer
		},
		methods:{
			run(){
				alert('父组件的方法')
			},
			change(){
				this.msg=this.$refs.footer.msg1;
				this.$refs.footer.run();
			},
			emitHome(){
				VueEvent.$emit('to-home',this.info1);
			}
		},
		mounted(){
			VueEvent.$on('to-news',data=>{
				console.log(data)
				this.info=data;
			})
		}
	}
</script>

<style>
</style>