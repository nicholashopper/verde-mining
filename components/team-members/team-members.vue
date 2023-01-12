<template>
  <div>
    <div class="row">
      <div class="column">
        <div class="card">
          <img src="/img/paul-avatar.jpg" alt="Luke" style="width:100%">
          <div class="container">
            <h2>Paul Cockerham</h2>
            <p class="title">Partner</p>
            <p>* 15 years of oil and gas industry experience</p>
            <p>* Operations Engineer</p>
          </div>
        </div>
      </div>
  
      <div class="column">
        <div class="card">
          <img src="/img/luis-avatar.jpg" alt="Luis" style="width:100%">
          <div class="container">
            <h2>Luis Caro-Delgado</h2>
            <p class="title">Partner</p>
            <p>* Pursuing a Ph.D. at UT Austin with an emphasis in Energy Systems-of-Systems</p>
            <p>* Over 18 years of local and international Oil and Gas industry</p>
          </div>
        </div>
      </div>

      <div class="column">
        <div class="card">
          <img src="/img/luke-avatar.jpg" alt="Luke" style="width:100%">
          <div class="container">
            <h2>Luke Hawkins</h2>
            <p class="title">Partner</p>
            <p>* Managed and executed numerous acquisitions and subsequent development of oil and gas properties across the Permian Basin</p>
          </div>
        </div>
      </div>

      <div class="column">
        <div class="card">
          <img src="/img/nicholas-avatar.jpg" alt="Nicholas" style="width:100%">
          <div class="container">
            <h2>Nicholas Hopper</h2>
            <p class="title">Partner</p>
            <p>* Over 5 years experience in software systems, monitoring, and data collection </p>
          </div>
        </div>
      </div>
  

      <div class="column">
        <div class="card">
          <img src="/img/matt-avatar.jpg" alt="Matt" style="width:100%">
          <div class="container">
            <h2>Matt Cain</h2>
            <p class="title">Field Technician</p>
         </div>
        </div>
      </div>

      <div class="column">
        <div class="card">
          <img src="/img/daniel-avatar.jpg" alt="Daniel" style="width:100%">
          <div class="container">
            <h2>Daniel Fernandez</h2>
            <p class="title">Intern</p>
            <p>Computer Science Student at UT Permian Basin</p>
            <p>&nbsp;</p>
          </div>
        </div>
      </div>
      
    
    </div>
  </div>
</template>

<script>
export default {
  name: "MyComponent"
};
</script>

<style scoped>
html {
  box-sizing: border-box;
}
*, *:before, *:after {
  box-sizing: inherit;
}
.column {
  float: left;
  width: 33.3%;
  margin-bottom: 16px;
  padding: 0 8px;
}
@media screen and (max-width: 650px) {
  .column {
    width: 100%;
    display: block;
  }
}
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}
.container {
  padding: 0 16px;
  height:200px;
  overflow:auto;
}
.container::after, .row::after {
  content: "";
  clear: both;
  display: table;
}
h2 {
  margin-top: 5px;
  margin-bottom: 5px;
}
p {
  margin-top: 5px;
  margin-bottom: 5px;
}
.title {
  margin-top: 5px;
  margin-bottom: 5px;
  color: #375d46;
}

</style>