<template>
	<section class="call-form">
		<div class="container call-form__container">
			<Title elementClass="call-form__title" :title="formTitle" />
			<form class="call-form__main">
				<input
					class="form-input"
					type="text"
					id="userName"
					placeholder="Your name"
					required
				/>
				<input
					class="form-input"
					type="tel"
					id="userTel"
					placeholder="Phone number"
					required
				/>
				<button class="org-btn" type="submit">
					Call Back<span class="org-btn__arrow material-symbols-outlined">
						trending_flat
					</span>
				</button>
			</form>
			<div class="call-form__img-wrapper">
				<img
					class="call-form__img"
					src="../assets/images/car.png"
					alt="delivery car"
				/>
			</div>
		</div>
	</section>
</template>

<script>
import Title from './Title.vue';

export default {
	components: {
		Title,
	},
	data() {
		return {
			formTitle: 'Fill out the formand we will call you',
		};
	},
};
</script>

<style lang="scss">
.form-input {
	width: 260px;
	height: 60px;
	background: #ffffff;
	border: 2px solid #eceef7;
	border-radius: 57px;
	font-weight: 400;
	font-size: 14px;
	line-height: 140%;
	color: #222222;
	padding: 20px 31px 19px;
}

.org-btn {
	width: 260px;
	height: 60px;
	background: linear-gradient(180deg, #fe5626 0%, #f23f0e 100%), #59aaf1;
	box-shadow: 0px 4px 8px rgba(205, 169, 41, 0.26);
	border-radius: 59px;
	font-weight: 700;
	font-size: 18px;
	line-height: 140%;
	text-align: center;
	color: #ffffff;
	display: flex;
	align-items: center;
	justify-content: center;
	gap: 20px;
	transition: all 0.4s ease;
	border: 2px solid transparent;

	&:hover {
		background: white;
		color: #fe5626;
		border: 2px solid #fe5626;
	}

	&__arrow {
		font-size: 50px;
	}
}

.call-form {
	background-image: url(../assets/images/form-bg.png);
	background-repeat: no-repeat;
	background-size: cover;
	background-position: top center;

	&__container {
		padding-top: 82px;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	&__title {
		margin-bottom: 42px;
		max-width: 505px;
	}

	&__main {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 37px;
	}

	&__img-wrapper {
		max-width: 684px;
		width: 100%;
	}

	&__img {
		width: 100%;
		object-fit: cover;
	}
}

@media screen and (min-width: 900px) {
	.call-form {
		&__main {
			flex-direction: row;
		}
	}
}
</style>
