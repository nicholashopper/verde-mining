<template>
    <main>
      <section v-if="posts" class="w-full max-w-5xl mx-auto">
        <h1 class="title">Events</h1>
        <posts post-type="events" :amount="10" />
      </section>
    </main>
  </template>
  
  <script>
  export default {
    async asyncData({ $content, error }) {
      let posts;
      try {
        posts = await $content("events").fetch();
      } catch (e) {
        error({ message: "Events not found" });
      }
      return { posts };
    },
  }
  </script>