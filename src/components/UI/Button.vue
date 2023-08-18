<template>
	<button>
		<slot></slot>
	</button>
</template>

<script>
	export default {
		name: 'my-button'
	}
</script>

<style scoped>
		.btn {
		margin-top: 15px; 
		padding: 10px 15px;
		border: 1px solid currentColor;
		background-color: transparent;
		color: #3399FF;;
		cursor: pointer;
	}
</style>