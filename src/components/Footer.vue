<template>
	<div>
		<h1>{{msg}}</h1>
		<button @click="change()">改变子组件</button>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				msg:'子组件',
				msg1:'我是子组件里面的值'
			}
		},
		methods:{
			run(){
				alert('子组件的方法')
			},
			change(){
				this.msg=this.$parent.msg1;
				this.$parent.run();
			}
		}
	}
</script>
 
<style>
</style>