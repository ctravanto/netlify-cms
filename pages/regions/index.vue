<template>
  <main>
    <section v-if="regions" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Regions</h1>
      <regions :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let regions;
    try {
      regions = await $content("region").fetch();
    } catch (e) {
      error({ message: "Regions not found" });
    }
    return { regions };
  },
}
</script>
