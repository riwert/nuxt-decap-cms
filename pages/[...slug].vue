<script setup lang="ts">

const route = useRoute()

const slugPath = route.params.slug
  ? Array.isArray(route.params.slug)
    ? '/' + route.params.slug.join('/')
    : '/' + route.params.slug
  : '/'

</script>

<template>
	<main id="main" class="home">
		<ContentDoc :path="slugPath">
      <template #default="{ doc }">
        <article>
          <h1>{{ doc.title }}</h1>
          <ContentRenderer :value="doc" />
        </article>
      </template>

			<template #empty>
        <h1>204</h1>
        <p>Brak zwartości.</p>
      </template>

      <template #not-found>
        <h1>404</h1>
        <p>Nie znaleziono strony.</p>
      </template>
    </ContentDoc>
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
