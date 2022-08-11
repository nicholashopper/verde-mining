<template>
  <main class="home-grid" >
    <section class="self-center items-center justify-center button-links">
      <header>
        <div class = "macAddress">
          <strong>Mac Address:</strong> 
          <br>{{response.id}}
        </div>
      </header>
      <body>
        <div class = "margin:3" v-for="(link, index) in links" :key="index">
          <button class="button" v-on:click="sendRequest(link.url, link.httpRequest)">{{link.name}}</button>
        </div>
      </body>
    </section>
  </main>
</template>

<script>
import axios from 'axios'

export default{

layout: 'customqr',

 async asyncData({params}){
  const {data} = await axios.get(`http://localhost:8080/qr-code/${params.id}`)
  data.links.forEach(link => {
      switch (link.type) {
        case "SETTINGS":
          link.name = "Settings"
          break;
        case "COMMAND":
          var arr = link.url.split("/");
          var len = arr.length;
          link.name = "/" + arr[len - 2] + "/" + arr[len - 1]
          break;
        case "HISTORY":
          link.name = "Notes"
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
 },
 methods:{
  sendRequest(url, httpRequest){
    if(httpRequest == "PATCH"){
      axios.patch(url)
        .then(response => {
          console.log(response.data)
        })
      .catch(error => {
        console.log(error)
      })
    }
    else if(httpRequest == "GET"){
      axios.get(url)
        .then(response => {
          console.log(response.data)
        })
      .catch(error => {
        console.log(error)
      })
    }
    else if(httpRequest == "SETTINGS"){
      location.assign(url)
    }
  }

  
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