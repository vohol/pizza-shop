<template>
	<section class="hero">
		<div class="container hero__container">
			<Title isMainTitle:true :title="heroTitle" elementClass="hero__title" />
			<p class="hero__description">
				{{ content }}
			</p>
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
	background-image: url(../assets/images/hero-bg.png);
	background-repeat: no-repeat;
	background-position: top center;
	background-size: cover;
	min-height: 100vh;

	&__container {
		padding-top: calc(74px + 90px); //74 - header height
	}

	&__title {
		margin-bottom: 18px;
	}

	&__description {
		max-width: 621px;
		text-align: center;
		margin: 0 auto;
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
