<template>
	<!-- Slider main container -->
	<div ref="swiper" class="swiper">
		<!-- Additional required wrapper -->
		<div class="swiper-wrapper">
			<!-- Slides -->
			<div v-for="photo in gallary" :key="photo.id" class="swiper-slide">
				<img
					class="slide__img"
					:src="require(`@/assets/images/${photo.img}`)"
					alt=""
				/>
			</div>
		</div>
	</div>
</template>

<script>
import Swiper, { Navigation, Pagination } from 'swiper';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

export default {
	data() {
		return {
			gallary: [
				{ id: 1, img: 'gal1.jpg' },
				{ id: 2, img: 'gal2.jpg' },
				{ id: 3, img: 'gal3.jpg' },
				{ id: 4, img: 'gal4.jpg' },
				{ id: 5, img: 'gal5.jpg' },
			],
		};
	},
	mounted() {
		new Swiper(this.$refs.swiper, {
			modules: [Navigation, Pagination],
			loop: true,
			slidesPerView: 1,
			spaceBetween: 20,
			centeredSlides: true,
			autoplay: {
				delay: 2500,
				disableOnInteraction: false,
			},
			breakpoints: {
				480: {
					slidesPerView: 2,
					spaceBetween: 30,
				},
				900: {
					slidesPerView: 3,
					spaceBetween: 40,
				},
				1300: {
					slidesPerView: 4.5,
					spaceBetween: 40,
				},
			},
		});
	},
};
</script>

<style lang="scss">
.swiper {
	max-width: 1440px;
	width: 100%;
}

.swiper-slide {
	max-width: 260px;
	position: relative;

	&::after {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		background: linear-gradient(
			0deg,
			rgba(37, 77, 124, 0.4),
			rgba(37, 77, 124, 0.4)
		);
	}

	&__img {
		object-fit: cover;
	}
}
</style>
