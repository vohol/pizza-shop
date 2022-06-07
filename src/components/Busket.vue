<template>
	<div class="busket">
		<span class="busket__amount">=158$</span>
		<div class="busket__icon-wrap">
			<svg class="busket__icon">
				<use xlink:href="../assets/images/sprite.svg#buy"></use>
			</svg>
		</div>
		<span class="busket__pcs">3</span>
	</div>
</template>

<script>
export default {
	name: 'busket-item',
};
</script>

<style lang="scss">
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
</style>
