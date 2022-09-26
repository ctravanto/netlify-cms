<template>
  <main>
    <section v-if="region">
      <nav class="mb-8" aria-label="go back">
        <router-back class="block" />
      </nav>

      <article>
        <img
          v-if="region.cover"
          class="cover-image"
          :src="region.cover"
        >
        <!-- <h6 class="inline py-1 px-2 mr-1 bg-gray text-white text-sm font-medium rounded-sm">{{ region.category }}</h6> -->
        <h1 class="">{{ region.title }}</h1>
        <p class="mt-1 mb-8 text-primary-600 dark:text-primary-400">{{ region.description }}</p>
        <nuxt-content :document="region" />
        <div v-if="region.showCarousel && region.gallery">
          HERE SHOULD BE A CAROUSEL WITH FOTOS, SINCE THIS IS AN EXAMPLE YOU ONLY GET WINNIE-POOH SLEEPING
          <img
              alt="winnie-pooh"
              class="image"
              :key="region.gallery[0].id"
              :src="image"
          />
        </div>
      </article>
    </section>
  </main>
</template>
<script>
export default {
  async asyncData({ $content, params, error }) {
    let region;
    try {
      region = await $content("region", params.region).fetch();
    } catch (e) {
      error({ message: "Region not found" });
    }
    return { region };
  },
}
</script>
