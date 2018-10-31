<template>
	<div>
		<h1>{{msg}}</h1>
		<button @click="change()">改变父组件</button>
		<v-foot ref='footer'></v-foot>
	</div>
</template>

<script>
	import Footer from './Footer.vue'
	export default{
		data(){
			return{
				msg:'父组件',
				msg1:'我是父组件里面的值'
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
				this.msg=this.$refs.footer.msg1
				this.$refs.footer.run();
			}
		}
	}
</script>

<style>
</style>