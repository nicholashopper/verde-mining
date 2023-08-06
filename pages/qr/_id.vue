<template>
  <main class="home-grid" >
    <section class="self-center items-center justify-center button-links">
      <header class = "macAddress" onclick=redirect()>
        <strong>Mac Address:</strong> 
        <br>12:34:00:00:00:01
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



<style>
.home-grid {
  background: url("assets/home-grid-v2.svg") no-repeat center bottom;
  height: 100vh;
  width: 100vw;
  position: relative;
}

.button-links {
  border-color: var(--border-color);
  border-width: thick;
  border-radius: 0.25rem;
  padding-top: 1rem;
  padding-right: 1rem;
  padding-bottom: 1rem;
  padding-left: 1rem;
  position: absolute;
  top: 12px;
  margin: 0;
  width: 90%;
  max-width: 320px;
}

div.macAddress{
  margin: 0 auto;
  margin-bottom: 15px;
  text-align: center;
  border-width: 3px;
  border-color:var(--border-color);
  border-radius: 1;
  padding-top: 1rem;
  padding-left: 1rem;
  padding-right: 1rem;
  padding-bottom: 1rem;
  max-width: 300px;

}

.button {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 5px auto;
    padding: 10px;
    background: #fff;
    border: 2px solid var(--border-color);
    border-radius: 3px;
    color: var(--border-color);
    font-family: "Quicksand", sans-serif;
    font-size: 1em;
    font-weight: 700;
    letter-spacing: 0.02em;
    line-height: 1;
    text-decoration: none;
    cursor: pointer;
    transition: 0.3s;
    text-align: center;
    max-width: 300px;
    width: 100%;
  }

  .button:hover {
    background: var(--border-color);
    color: #fff;
  }
</style>