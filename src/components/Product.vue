<template>
	<div class="product">
		<div class="product__img-wrap">
			<img
				class="product__img"
				:src="require(`@/assets/images/${product.photo}`)"
				:alt="product.name"
			/>
		</div>
		<div class="product__title-wrapper">
			<h3 class="product__title">{{ product.name }}</h3>
			<span class="product__size">{{ product.size }}</span>
		</div>
		<span class="product__description">{{ product.compound }}</span>
		<span class="product__price">{{ product.price }} UAH</span>
		<button
			@click="
				buy();
				pulse($event);
			"
			class="buy-btn product__buy-btn"
		>
			<svg class="buy-btn__icon">
				<use xlink:href="../assets/images/sprite.svg#buy"></use>
			</svg>
		</button>
	</div>
</template>

<script>
export default {
	name: 'product-item',
	props: ['product'],
	methods: {
		buy() {
			this.$emit('buy', this.product);
		},
		pulse(event) {
			const target = event.target;
			target.classList.add('pulse');
			setTimeout(() => {
				target.classList.remove('pulse');
			}, 800);
		},
	},
};
</script>

<style lang="scss">
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

	&:hover {
		border: 2px solid #f58656;
	}
	&.pulse {
		animation: pulse 1s forwards ease-out;
		box-shadow: 0px 15px 28px -11px rgba(#f58656, 0.9);
	}

	&__icon {
		pointer-events: none;
		width: 12.08px;
		height: 14px;
	}
}

@keyframes pulse {
	0% {
		-moz-box-shadow: 0 0 0 0 rgba(#f58656, 0.4);
		box-shadow: 0 0 0 0 rgba(#f58656, 0.4);
	}
	70% {
		-moz-box-shadow: 0 0 0 30px rgba(255, 79, 93, 0);
		box-shadow: 0 0 0 30px rgba(255, 79, 93, 0);
	}
	100% {
		-moz-box-shadow: 0 0 0 0 rgba(255, 79, 93, 0);
		box-shadow: 0 0 0 0 rgba(255, 79, 93, 0);
	}
}

.product {
	display: flex;
	flex-direction: column;
	align-items: center;
	width: 260px;
	height: 418px;
	padding: 36px 15px 0 25px;
	position: relative;
	border-radius: 15px;
	background-image: url(../assets/images/card-bg.png);

	&__img-wrap {
		width: 170px;
		height: 173px;
		margin-bottom: 30px;
	}

	&__img {
		width: 100%;
		height: 100%;
		object-fit: contain;
		filter: drop-shadow(20px 10px 20px rgba(143, 92, 32, 0.1))
			drop-shadow(10px 5px 10px rgba(143, 92, 32, 0.1));
	}

	&__title-wrapper {
		width: 100%;
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 8px;
	}

	&__title {
		font-weight: 600;
		font-size: 16px;
		line-height: 140%;
		color: #000000;
	}

	&__description,
	&__size {
		font-weight: 400;
		font-size: 12px;
		line-height: 140%;
		color: #000000;
	}

	&__description {
		margin-bottom: 19px;
	}

	&__price {
		font-weight: 300;
		font-size: 24px;
		line-height: 140%;
		text-align: center;
		color: #121146;
		margin-bottom: 37px;
	}
}
</style>
