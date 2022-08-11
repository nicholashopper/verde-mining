<template>
  <main class="home-grid wrapper" >
    <section class="self-center items-center justify-center button-links">
      <header>
        <div class = "a">
          <strong>Mac Address:</strong> 
          <br>{{response.id}}
        </div>
      </header>
      <body>
        <div v-for="(link, index) in links" :key="index">
          <Button class="justify-center" v-on:click="sendRequest(link.url, link.httpRequest)" :href="link.url">
            {{link.name}}
          </Button>
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
      axios.patch(link.url)
        .then(response => {
          console.log(response.data)
        })
      .catch(error => {
        console.log(error)
      })
    }
    else if(httpRequest == "GET"){
      axios.get(link.url)
        .then(response => {
          console.log(response.data)
        })
      .catch(error => {
        console.log(error)
      })
    }
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
  position: absolute;
  top: 12px;
  margin: 0;
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