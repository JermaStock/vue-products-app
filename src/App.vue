<template>
	<div class="app">
		<h1 class="main-title">Список продуктов</h1>
		<product-form
			@create="addProduct"
		/>
		<product-list
			:products="products"
			@strikeout="strikeoutProduct"
		/>
	</div>
</template>

<script>
	import ProductForm from './components/ProductForm.vue';
	import ProductList from './components/ProductList.vue';

	if (!localStorage.getItem('product-storage')) {
		localStorage.setItem('product-storage', JSON.stringify([]));
	}

	export default {
		components: {
			ProductForm, ProductList
		},
		data() {
			return {
				products: JSON.parse(localStorage.getItem('product-storage'))
			}
		},
		methods: {
			addProduct(product) {
				this.products.unshift(product);
				localStorage.setItem('product-storage', JSON.stringify(this.products));
			},
			strikeoutProduct(product) {
				if (product.purchased) {
					return;
				}
				this.products = [...this.products.filter(p => p.id !== product.id), {...product, purchased: true}];
				localStorage.setItem('product-storage', JSON.stringify(this.products));
			}
		}
	}
</script>

<style>
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
		color: #333;
	}

	:root {
		background-color: linen;
	}

	.app {
		padding: 20px;
		margin: 0 auto;
		max-width: 550px;
	}

	.main-title {
		text-align: center;
		font-size: 2rem;
		margin-bottom: 30px;
	}

</style>