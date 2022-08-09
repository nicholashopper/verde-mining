<template>
  <main>
    <section class="self-center items-center justify-center button-links">
      <header>
        <div class = "a">
          <strong>Mac Address:</strong> 
          <br>{{links.id}}
        </div>
      </header>
      <body>
        
        <li v-for="link in links">
           <div>
           <a class="linkbutton justify-center items-center" v-bind:href="link.url">{{ link.name }}</a>
          </div>
        </li>
        <div>
          <a class="linkbutton justify-center items-center" v-bind:href="links[0].url">Settings</a>
        </div>
        <div>
          <a class="linkbutton justify-center items-center" v-bind:href="links[1].url">/lights/on</a>
        </div>
        <div>
          <a class="linkbutton justify-center items-center" v-bind:href="links[2].url">/lights/off</a>
        </div>
        <div>
          <a class="linkbutton justify-center items-center" v-bind:href="links[3].url">Notes</a>
        </div>
      </body>
    </section>
  </main>
</template>

<script>
import axios from 'axios'

export default{

 


 async asyncData({params}){
  const {data} = await axios.get(`http://localhost:8080/qr-code/${params.id}`)
  data.links.forEach(link => {
      switch (link.type) {
        case "SETTINGS":
          link.name = "Settings"
          break;
      
        default:
          link.name = link.url
          break;
      }
    });
  return{
   response: data,
   links: data.links
  }
 }
}
</script>



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