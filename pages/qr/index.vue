<template>
  <main class = "home-grid">
    <section class="self-center items-center justify-center button-links">
      <header>
        <div class = "a">
          <strong>Mac Address:</strong> 
          <br>{{notes.id}}
        </div>
      </header>
      <body>
        <div>
          <a class="linkbutton justify-center items-center" v-bind:href="notes.links[0].url">Settings</a>
        </div>
        <div>
          <a class="linkbutton justify-center items-center" v-bind:href="notes.links[1].url">/lights/on</a>
        </div>
        <div>
          <a class="linkbutton justify-center items-center" v-bind:href="notes.links[1].url">/lights/off</a>
        </div>
        <div>
          <a class="linkbutton justify-center items-center" v-bind:href="notes.links[2].url">Notes</a>
        </div>
      </body>
    </section>
  </main>
</template>

<script>
 import axios from 'axios'

 export default {
  async asyncData() {
  const {data} = await axios.get('http://localhost:8080/qr-code/12%3A34%3A00%3A00%3A00%3A01')
   return {
    notes: data
   }
  }
 }
</script>

<!-- <script>
 import { MDBBtn } from 'mdb-vue-ui-kit'

  export default {
      MDBBtn
   
  }
</script> -->




<style>
.home-grid {
  background: url("assets/home-grid-v2.svg") no-repeat center bottom;
  width: 100%;
  position: relative;
}

.button-links {
  border-color: var(--border-color);
  border-width: thin;
  border-radius: 0.25rem;
  padding-top: 1rem;
  padding-right: 1rem;
  padding-bottom: 1rem;
  padding-left: 1rem;

}

input, label, textarea {
    display: ruby-base-container;
    width: 100%;
    
}

.mac-address{
  text-size-adjust: 30px;
}

div.a{
  text-align: center;
  border-width: thin;
  border-color:var(--border-color);
  border-radius: 1;
  padding-top: 1rem;
  padding-left: 1rem;
  padding-right: 1rem;
  padding-bottom: 1rem;
}

.linkbutton {
  display: inline-flex;
  padding: 10px;
  margin: 5px;
  background: var(--border-color);
  width: 200px;
  text-align: center;
  color: #000000;
}
</style>