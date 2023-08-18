<template>
	<div v-if="products.length">
		<h3>Список продуктов:</h3>
		<product-item 
			v-for="product in products"
			:product="product"
			:key="product.id"
			@strikeout="$emit('strikeout', product)"
		>
		</product-item>
	</div>
	<h2 v-else style="text-align: center;">
		Список продуктов пуст
	</h2>
</template>

<script>
import ProductItem from './ProductItem.vue';

export default {
	components: {
		ProductItem,
	},
	props: {
		products: {
			type: Array,
			required: true,
		}
	}
}
</script>

<style scoped>

</style>