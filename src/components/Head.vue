<template>
	<div class="head">
		{{msg}}
	</div>
</template>
<script>
	export default{
		name:'head',
		data(){
			return{
				msg:'touch'
			}
		}
	}
</script>
<style>
	.head{
		position: fixed;
		top: 0;
		z-index: 1000;
		width: 100%;
		height: 60px;
		line-height: 60px;
		background: #ED4D2A;
		color: #ffffff;
		font-size: 24px;
	}
</style>