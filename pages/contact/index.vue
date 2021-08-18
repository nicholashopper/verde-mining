<template>
  <main class="home-grid">
    <section class="self-center flex-col items-left contact-form">
      <h2 class="">
        Contact
      </h2>
      <form name="contact" method="POST" netlify>
        <p>
          <label class="mt-1 mb-8 text-primary-600 dark:text-primary-400">Your Name: <input type="text" name="name" /></label>   
        </p>
        <p>
          <label class="mt-1 mb-8 text-primary-600 dark:text-primary-400">Your Email: <input type="email" name="email" /></label>
        </p>
        <p>
          <label class="mt-1 mb-8 text-primary-600 dark:text-primary-400">Message: <textarea name="message"></textarea></label>
        </p>
        <p>
          <button type="submit" class="btn block" >Send</button>
        </p>
      </form>
    </section>
  </main>
</template>

<script>
export default {

}
</script>

<style>
.home-grid {
  background: url("assets/home-grid-v2.svg") no-repeat center bottom;
  width: 100%;
}

.contact-form {
  border-color: var(--border-color);
  border-width: thin;
  border-radius: 0.25rem;
  padding-top: 1rem;
  padding-right: 1rem;
  padding-bottom: 1rem;
  padding-left: 1rem;
}

input, label, textarea {
    display: block;
    width: 100%;
}
</style>
