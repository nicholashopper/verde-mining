<template>
    <main>
      <section v-if="teamMembers" class="w-full max-w-5xl mx-auto">
        <h1 class="title">Meet Our Team</h1>
        <team-members post-type="team" :amount="10" />
      </section>
    </main>
  </template>
  
  <script>
  export default {
    async asyncData({ $content, error }) {
      let teamMembers;
      try {
        teamMembers = await $content("team").fetch();
      } catch (e) {
        error({ message: "Team members found" });
      }
      return { teamMembers };
    },
  }
  </script>


  
  