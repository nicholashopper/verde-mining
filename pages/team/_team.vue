<template>
    <div>
      <h1>Meet Our Team</h1>
      <div v-for="teamMember in teamMembers" :key="teamMember.name" class="team-member">
        <img :src="teamMember.avatar" alt="Avatar for {{ teamMember.name }}" class="avatar" />
        <h3>{{ teamMember.name }}</h3>
        <p>{{ teamMember.title }}</p>
      </div>
    </div>
  </template>

<script>
export default {
  async asyncData({ $content, error }) {
    let teamMembers
    try {
      teamMembers = await $content('team').fetch()
    } catch (e) {
      error({ message: "Team members not found" })
    }
    return { teamMembers }
  }
}


</script>

<style>
.team-member {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

.avatar {
  width: 500px;
  height: 500px;
  border-radius: 50%;
  margin-right: 1rem;
}
</style>