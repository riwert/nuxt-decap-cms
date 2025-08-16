<script lang="ts" setup>

const route = useRoute()

const { data: page } = await useAsyncData(route.path, () => {
  return queryCollection('content').path(route.path).first()
})

setSeoHead(home.SEOmetaData);

</script>

<template>
	<main id="main" class="home">
		<ContentRenderer v-if="page" :value="page" />
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
