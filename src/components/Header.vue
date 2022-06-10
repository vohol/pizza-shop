<template>
	<header class="header">
		<div class="container header__container">
			<Navigation />
			<Logo elementClass="header__logo" />
			<div class="header__right">
				<div
					class="header__work-time"
					:class="{ 'header__work-time--active': checkWorking() }"
				>
					Daily {{ workHours.openTime }}am - {{ workHours.closeTime }}pm
				</div>
				<a class="header__tel" href="tel:800330898"
					><span class="icon material-symbols-outlined"> phone_in_talk </span>0
					800 33 08 98</a
				>
			</div>
		</div>
	</header>
</template>

<script>
import Navigation from './Navigation.vue';
import Logo from './Logo.vue';

export default {
	name: 'headerItem',
	components: {
		Navigation,
		Logo,
	},
	created() {
		window.addEventListener('scroll', this.handleScroll);
	},
	destroyed() {
		window.removeEventListener('scroll', this.handleScroll);
	},
	data() {
		return {
			workHours: {
				openTime: 8,
				closeTime: 9,
			},
		};
	},
	methods: {
		checkWorking() {
			let time = new Date();
			let userTime = time.getHours();
			let status;
			userTime >= this.workHours.openTime &&
			userTime < this.workHours.closeTime + 12
				? (status = true)
				: (status = false);

			return status;
		},
		handleScroll() {
			const className = 'has-background';
			const scrollTrigger = 50;
			const header = document.querySelector('.header');

			if (
				window.scrollY >= scrollTrigger ||
				window.pageYOffset >= scrollTrigger
			) {
				header.classList.add(className);
			} else {
				header.classList.remove(className);
			}
		},
	},
};
</script>

<style lang="scss">
.header {
	position: fixed;
	top: 0;
	right: 0;
	left: 0;
	background: transparent;
	z-index: 999;
	transition: background-color 0.3s ease;

	&__container {
		padding-top: 15px;
		padding-bottom: 15px;
		display: grid;
		grid-template-columns: 2fr 1fr 2fr;
	}

	&__right {
		display: flex;
		align-items: center;
		justify-content: flex-end;
		gap: 40px;
	}

	&__work-time {
		display: none;
		align-items: center;
		font-weight: 400;
		font-size: 16px;
		line-height: 1.25;
		color: #000000;

		&::before {
			content: ' ';
			display: inline-block;
			width: 4px;
			height: 4px;
			border-radius: 50px;
			margin-right: 9px;
			background-color: red;
		}

		&--active::before {
			background-color: #46cb72;
		}
	}

	&__tel {
		display: flex;
		align-items: center;
		gap: 6px;
		font-family: 'Montserrat';
		font-weight: 700;
		font-size: 12px;
		line-height: 1;
		color: #000000;

		.icon {
			display: flex;
			align-items: center;
			justify-content: center;
			width: calc(33px * 0.4);
			height: calc(33px * 0.4);
			font-size: 8px;
			color: white;
			background: linear-gradient(287.74deg, #f58656 8.52%, #fe5626 92.72%);
			box-shadow: 0px 4px 8px rgba(205, 169, 41, 0.26);
			border-radius: 59px;
		}
	}
}

@media screen and (min-width: 1000px) {
	.header {
		&__container {
			display: grid;
			grid-template-columns: 3fr 1fr 3fr;
			padding-top: 25px;
		}

		&__right {
			display: flex;
		}

		&__work-time {
			display: flex;
			font-size: 16px;
		}

		&__tel {
			gap: 16px;
			font-size: 18px;

			.icon {
				width: 33px;
				height: 33px;
				font-size: 14px;
			}
		}
	}
}

.has-background {
	background: #f0f5fb;
}
</style>
