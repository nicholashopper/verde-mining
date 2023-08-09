<template>
  <main class="home-grid" >
    <section class="self-center items-center justify-center button-links">
      <header class = "macAddress" onclick=redirect()>
      </header>
    </section>
  </main>
</template>

<script>
export default{

layout: 'customqr',
async asyncData({ redirect, params }) {
  const customURL = `https://script.google.com/a/macros/verdemining.com/s/AKfycbyH2U2vyD4mTvoXSlQy51Ob60mgalCUBKTVSuCq5i2eWPwLhk0WdM7P8VmB0byvkLuw/exec?minerID=${params.id}`;
  redirect(customURL);
}
}
</script>