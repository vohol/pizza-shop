<template>
	<section class="instagram">
		<GallarySwiper />
		<a class="inst-link" :href="instagrammAccount.link"
			>Instagram:
			<span class="inst-link__account">{{ instagrammAccount.name }}</span></a
		>
	</section>
</template>

<script>
import GallarySwiper from './GallarySwiperB.vue';
export default {
	name: 'instagramm-section',
	components: { GallarySwiper },
	data() {
		return {
			instagrammAccount: {
				name: '@classic_kovel',
				link: '#',
			},
		};
	},
};
</script>

<style lang="scss">
.instagram {
	position: relative;
	margin-bottom: 127px;
}

.inst-link {
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	z-index: 1;
	display: block;
	max-width: 480px;
	width: 100%;
	height: 180px;
	background: linear-gradient(45.04deg, #fd9924 -51.05%, #f65b16 134.89%);
	box-shadow: 0px 70px 90px rgba(253, 55, 36, 0.2),
		0px 35px 50px rgba(253, 55, 36, 0.2), 0px 20px 25px rgba(253, 55, 36, 0.2);
	border-radius: 15px;
	font-weight: 400;
	font-size: 24px;
	line-height: 29px;
	color: #ffffff;
	display: flex;
	align-items: center;
	justify-content: center;

	&__account {
		font-weight: 700;
	}

	&::after {
		display: none;
		content: '';
		position: absolute;
		opacity: 0.1;
		border: 2px solid #ffffff;
		border-radius: 15px;
		max-width: 440px;
		width: 100%;
		height: 140px;

		@media screen and (min-width: 480px) {
			display: block;
		}
	}
}
</style>
