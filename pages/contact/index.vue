<template>
  <main>
    <section class="self-center flex flex-col flex-1 items-center">
      <h1 class="title">
        Contact
      </h1>
      <form name="contact" method="POST" data-netlify="true" netlify-honeypot="bot-field" netlify>
        <div class="items-right">
          <p class="hidden">     
            <label>Don’t fill this out: <input name="bot-field"></label>   
          </p>
          <p>
            <label>Your Name: <input type="text" name="name" /></label>   
          </p>
          <p>
            <label>Your Email: <input type="email" name="email" /></label>
          </p>
          <!-- <p>
            <label>Your Role: <select name="role[]" multiple>
              <option value="leader">Leader</option>
              <option value="follower">Follower</option>
            </select></label>
          </p>  -->
          <p>
            <label>Message: <textarea name="message"></textarea></label>
          </p>
        </div>
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
