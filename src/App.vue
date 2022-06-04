<template>
	<div id="app">
		<Header />
		<main>
			<Hero />
			<Shop />
		</main>
	</div>
</template>

<script>
import Header from './components/Header.vue';
import Hero from './components/Hero.vue';
import Shop from './components/Shop.vue';

export default {
	name: 'App',
	components: {
		Header,
		Hero,
		Shop,
	},
};
</script>

<style lang="scss">
@use '../src/assets/scss/nullstyle.scss' as *;

.material-symbols-outlined {
	font-variation-settings: 'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 48;
}

body {
	font-family: 'Montserrat', sans-serif;
}

.container {
	max-width: 1200px;
	width: 100%;
	padding-right: 20px;
	padding-left: 20px;
	margin: 0 auto;
}
</style>
