<template>
	<footer class="footer">
		<div class="container footer__container">
			<span class="footer__span"> &copy; {{ ownerGroup }}</span>
			<Logo elementClass="footer__logo" />
			<span class="footer__span"
				>Made with delight by
				<a class="footer__link" href="#">{{ siteCreater }}</a>
			</span>
		</div>
	</footer>
</template>

<script>
import Logo from './Logo.vue';
export default {
	name: 'footer-item',
	components: { Logo },
	data() {
		return {
			ownerGroup: 'Classic Family Restaurant',
			siteCreater: 'harmuder',
		};
	},
};
</script>

<style lang="scss">
.footer {
	&__container {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 30px;
		padding-bottom: 50px;
	}

	&__logo {
		order: -1;
	}

	&__span {
		font-weight: 400;
		font-size: 14px;
		line-height: 140%;
		color: #000000;
	}

	&__link {
		font-weight: 700;
		font-size: 14px;
		line-height: 140%;
		color: #000000;
		transition: color 0.2s ease;

		&:hover {
			color: #f58656;
		}
	}
}

@media screen and (min-width: 900px) {
	.footer {
		&__container {
			flex-direction: row;
			align-items: center;
			justify-content: space-between;
			gap: 0;
		}

		&__logo {
			order: 0;
		}

		&__span {
			font-size: 16px;
		}

		&__link {
			font-size: 16px;
		}
	}
}
</style>
