<script setup>
const { data: index } = reactive(await useAsyncData("index", () =>
	queryContent("/index").findOne())
);

// setSeoHead(index?.SEOmetaData);
</script>

<template>
	<main id="main" class="index">
		<MDC :value="index" />
	</main>

</template>

<style lang="scss" scoped>
main {
	display: grid;
	justify-items: center;
	align-items: center;
	:deep(div) {
		max-width: 50em;
	}
	// assets/scss/mixins
	@include fade-in;
}
</style>
