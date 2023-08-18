<template>
	<div 
		@click="$emit('strikeout', product)"
		class="product"
	>
		<div
			:class="{strikeout: product.purchased}"
		><strong>Наименование: </strong>{{ product.name }}</div>
	</div>
</template>

<script>
export default {
	props: {
		product: {
			type: Object,
			required: true,
		}
	}
}
</script>

<style scoped>

.product {
	margin-top: 15px;
	padding: 15px;
	border: 2px solid #3399FF;
	cursor: pointer;
}

.strikeout {
	text-decoration: line-through;
}
</style>