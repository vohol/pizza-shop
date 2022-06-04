<template>
	<h1 v-if="isMainTitle" :class="elementClass" class="section-title">
		{{ title }}
	</h1>
	<h2 v-else :class="elementClass" class="section-title">{{ title }}</h2>
</template>

<script>
export default {
	name: 'section-title',
	props: {
		title: String,
		elementClass: String,
		isMainTitle: {
			type: Boolean,
			default: false,
		},
	},
};
</script>

<style lang="scss">
.section-title {
	font-weight: 700;
	font-size: 28px;
	line-height: 1.22;
	text-align: center;
	color: #000000;
}

@media screen and (min-width: 1000px) {
	.section-title {
		font-size: 48px;
	}
}
</style>
