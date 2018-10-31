<template>
	<div>
		<h1>我是头部--{{msg}}</h1>
		<button @click="getData">点击</button>
	</div>
</template>

<script>
export default{
	data(){
		return{
			
		}
	},
	props:['msg','getData','home']
}
</script>

<style lang="scss" scoped="scoped">
h1{ background: #2C3E50; color: #fff;}
</style>