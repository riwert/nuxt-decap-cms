<script setup>
const route = useRoute();

const { data: product } = reactive(await useAsyncData("product", () =>
	queryContent("/products", route.params.slug).findOne())
);
</script>

<template>
	<main :key="setLocale">
		<div class="singular-product">
			<h1>{{ product.title }}</h1>
			<blockquote>{{ product.description }}</blockquote>
			<MediaRespImage :url="product.image" :lightbox="true" />
			<MDC :value="product" />
		</div>
	</main>
</template>

<style lang="scss">
.singular-product {
	max-width: 45em;
	margin-inline: auto;
	img {
		position: relative;
		width: 100%;
	}
}
</style>
