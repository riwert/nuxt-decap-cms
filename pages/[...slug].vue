<script setup lang="ts">

const route = useRoute()

const slugPath = '/' + (route.params.slug ? route.params.slug.join('/') : 'pages')

const { data: page } = await useAsyncData(`page-${slugPath}`, () =>
  queryContent('pages').where({ _path: slugPath }).findOne()
)

// setSeoHead(page.SEOmetaData);

</script>

<template>
	<main id="main" class="home">
		<h1 v-if="page.title">{{ page.title }}</h1>
		<MDC v-if="page.content" :value="page.content" />
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
