<template>
	<section class="shop">
		<div class="container shop__container">
			<div class="busket-wrapper">
				<div class="busket">
					<span class="busket__amount">= {{ gerBusketSumm }} UAH</span>
					<div class="busket__icon-wrap">
						<svg class="busket__icon">
							<use xlink:href="../assets/images/sprite.svg#buy"></use>
						</svg>
					</div>
					<span class="busket__pcs">{{ gerBusketQty }}</span>
				</div>
			</div>
			<Title elementClass="shop__title" :title="shopTitle" />
			<ul class="shop__filters">
				<li
					v-for="filter in filterList"
					:key="filter"
					@click="filterToggle"
					class="shop__filter"
				>
					{{ filter }}
				</li>
			</ul>
			<ul class="shop-list">
				<li v-for="item in getPaginatedProducts" :key="item.id">
					<Product :product="item" @buy="addProductToBucket" />
				</li>
			</ul>
			<button @click="loadMore" class="update">
				<svg class="update__icon">
					<use xlink:href="../assets/images/sprite.svg#update"></use>
				</svg>
			</button>
		</div>
	</section>
</template>

<script>
import Title from './Title.vue';
import Product from './Product.vue';
import * as d from '../data.js';

export default {
	name: 'shopItem',
	components: {
		Title,
		Product,
	},
	data() {
		return {
			shopTitle: 'Popular dishes',
			allProducts: d.defaultData,
			activeFilters: [],
			busketData: [],
			productsToShow: 8,
		};
	},
	methods: {
		addProductToBucket(product) {
			let result = false;

			this.busketData.forEach((element) => {
				if (element.id == product.id) {
					element.qty++;
					result = true;
					return;
				}
			});

			if (result) return;

			this.busketData.push({ ...product, qty: 1 });
		},
		filterToggle(event) {
			let target = event.target.textContent.trim();
			let targetObject = event.target;

			if (this.activeFilters.includes(target)) {
				this.activeFilters = this.activeFilters.filter(
					(element) => element != target
				);
				targetObject.classList.remove('shop__filter--active');
			} else {
				this.activeFilters.push(target);
				targetObject.classList.add('shop__filter--active');
			}
		},
		loadMore() {
			if (this.productsToShow > this.getPaginatedProducts) return;
			this.productsToShow += 8;
		},
	},
	computed: {
		//function to get all product
		getProducts: function () {
			let products = this.allProducts;
			return products;
		},
		//function to generate filters
		filterList: function () {
			let newArray = [];

			this.getProducts.forEach((element) => {
				if (!newArray.includes(element.category)) {
					newArray.push(element.category);
				}
			});

			return newArray;
		},
		//function to show product according active filters
		filteredProducts: function () {
			let filteredItems = [];

			if (this.activeFilters.length == 0) {
				filteredItems = this.getProducts;
			}

			this.getProducts.forEach((element) => {
				if (this.activeFilters.includes(element.category)) {
					filteredItems.push(element);
				}
			});

			return filteredItems;
		},
		getPaginatedProducts: function () {
			return this.filteredProducts.slice(0, this.productsToShow);
		},

		gerBusketSumm: function () {
			return this.busketData.reduce(
				(prev, curr) => prev + curr.qty * curr.price,
				0
			);
		},
		gerBusketQty: function () {
			return this.busketData.reduce((prev, curr) => prev + curr.qty, 0);
		},
	},
};
</script>

<style lang="scss">
.shop {
	&__container {
		padding-top: 31px;
		padding-bottom: 103px;
		position: relative;
	}

	&__title {
		margin-bottom: 49px;
	}

	&__filters {
		display: flex;
		justify-content: center;
		gap: 30px;
		margin-bottom: 50px;
	}

	&__filter {
		cursor: pointer;
		min-width: 135px;
		background: #eceef6;
		border-radius: 45px;
		padding: 16px;
		font-weight: 600;
		font-size: 16px;
		line-height: 140%;
		text-align: center;
		text-transform: capitalize;
		transition: background 0.2s;

		&--active {
			background: #59aaf1;
		}
	}
}

.busket-wrapper {
	position: absolute;
	top: -50px;
	right: 15px;
}

@media screen and (min-width: 700px) {
	.busket-wrapper {
		top: 15px;
	}
}

.busket {
	display: flex;
	align-items: center;
	position: relative;

	&__amount {
		display: inline-block;
		padding: 10px 15px;
		border-radius: 10px;
		color: white;
		font-weight: 600;
		font-size: 16px;
		line-height: 140%;
		background-color: #3f3f3f;
		margin-right: 10px;
	}

	&__icon-wrap {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 80px;
		height: 80px;
		border-radius: 50%;
		box-shadow: 0 0 20px 4px rgba(#000000, 0.3);
	}

	&__icon {
		width: 36px;
		height: 42px;
	}

	&__pcs {
		display: flex;
		align-items: center;
		justify-content: center;
		position: absolute;
		right: 0;
		bottom: 0;
		width: 30px;
		height: 30px;
		border-radius: 50%;
		background-color: #f58656;
		color: white;
	}
}

.buy-btn {
	display: flex;
	align-items: center;
	justify-content: center;
	position: absolute;
	left: 50%;
	bottom: 8px;
	transform: translate(-50%);
	z-index: 10;
	width: 33px;
	height: 33px;
	border-radius: 50%;
	background-color: white;
	border: 2px solid #eceef6;

	&__icon {
		width: 12.08px;
		height: 14px;
	}
}

.shop-list {
	display: flex;
	flex-direction: column;
	align-items: center;
	gap: 40px;
	margin-bottom: 40px;
}

@media screen and (min-width: 600px) {
	.shop-list {
		display: grid;
		grid-template-columns: 1fr 1fr;
		justify-items: center;
		gap: 40px;
		max-width: 560px;
		margin: 0 auto;
		margin-bottom: 66px;
	}
}

@media screen and (min-width: 1200px) {
	.shop-list {
		grid-template-columns: 1fr 1fr 1fr 1fr;
		max-width: 1160px;
	}
}

.update {
	width: 60px;
	height: 60px;
	margin: 0 auto;
	display: flex;
	align-items: center;
	justify-content: center;
	background: linear-gradient(287.74deg, #f58656 8.52%, #fe5626 92.72%);
	box-shadow: 0px 4px 8px rgba(205, 169, 41, 0.26);
	border-radius: 59px;

	&__icon {
		width: 25px;
		height: 25px;
	}
}
</style>
