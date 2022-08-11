<template>
  <main class="home-grid">
    <section class="self-center flex flex-col flex-1 items-center justify-center">
      <!-- <h1 class="title text-center">Verde Mining</h1>
      <h2 class="subtitle text-center">Bitcoin Tech</h2> -->
      <img class="banner" src="/img/verde-logos/VerdeMining-Logo-Vertical.png"/>
    </section>
    <!-- <section class="mt-8 content-box">
      <h3 class="text-primary-600 dark:text-primary-400 max-w-5xl mx-auto">Latest Project</h3>
      <posts post-type="projects" :amount="1" />
    </section> -->
  </main>
</template>

<style>
.home-grid {
  background: url("assets/home-grid-v2.svg") no-repeat center bottom;
  /* background-size: cover; */
  width: 100%;
}

.banner {
  width: 40%;
}

.content-box {
  background-color: var(--bg);
}
</style>