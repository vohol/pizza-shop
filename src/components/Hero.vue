<template>
	<section class="hero">
		<div class="container hero__container">
			<Title isMainTitle:true :title="heroTitle" elementClass="hero__title" />
			<p class="hero__description">
				{{ content }}
			</p>
			<div class="hero__img-wrapper">
				<img class="hero__img" src="../assets/images/piza-main.png" alt="" />
			</div>
		</div>
	</section>
</template>

<script>
import Title from './Title.vue';

export default {
	name: 'hero-section',
	components: {
		Title,
	},
	data() {
		return {
			content:
				'If you decide to relax or have unexpected guests, call us. We make sure that your vacation is comfortable, enjoyable and delicious',
			heroTitle: 'Food delivery in Kovel',
		};
	},
};
</script>

<style lang="scss">
.hero {
	position: relative;
	background-image: url(../assets/images/hero-bg.png);
	background-repeat: no-repeat;
	background-position: top center;
	background-size: cover;
	height: calc(100vh - 130px);
	margin-bottom: 130px;

	&__container {
		padding-top: calc(74px + 90px); //74 - header height
	}

	&__title {
		margin-bottom: 18px;
		position: relative;
		z-index: 1;
	}

	&__description {
		max-width: 621px;
		text-align: center;
		margin: 0 auto;
		position: relative;
		z-index: 1;
	}

	&__img-wrapper {
		max-width: 667px;
		width: 100%;
		position: absolute;
		right: 50%;
		bottom: -100px;
		transform: translateX(50%);
	}

	&__img {
		width: 100%;
	}
}

@media screen and (min-width: 1000px) {
	.hero {
		&__container {
			padding-top: calc(107px + 90px); //74 - header height
		}
	}
}
</style>
