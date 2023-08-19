<template>
	<form class="form" @submit.prevent>
		<my-input 
			v-model="product.name"
			placeholder="Название продукта"
		/>
		<my-button 
			class="btn" 
			@click="addProduct"
		>
			Добавить продукт
		</my-button>
	</form>
</template>

<script>
export default {
	data() {
		return {
			product: {
				name: ''
			}
		}
	},
	methods: {
		addProduct() {
			this.product.id = Date.now();
			this.product.purchased = false;
			this.$emit('create', this.product)
			this.product = {
				name: '',
			}
		}
	}
}
</script>

<style scoped>
	.form {
		display: flex;
		flex-direction: column;
	}

	.form__title {
		text-align: center;
		font-size: 1.5rem;
	}

	.btn {
		align-self: center;
	}
</style>