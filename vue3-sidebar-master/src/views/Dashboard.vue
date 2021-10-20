<template>
 <div class="header">
   <br>
  <h3><b><i> Posljednje novosti vezane za Crypto </i></b></h3>
  <p> <i> <b> Crypto Novosti </b> </i> </p>

</div>
<br><br><br>
  <section class="section">	 
 <div class="card mb-3" style="max-width: 540px;" v-for="item in news" v-bind:key="item in news">
  <div class="row g-0">
   <div class="col-md-4">
      <img v-bind:src="item.imageurl" class="img-fluid rounded-start" alt="...">
    </div>
     <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title"> <b> {{item.title}} </b></h5>
        <p class="card-text">{{item.body}}</p>
        <p class="card-text"><small class="text-muted">{{source}}</small></p>
		      <a type="button" class="btn btn-primary" v-bind:href="item.guid" > Saznaj vise...</a>
      </div>
    </div>
  </div>
</div>
</section>
</template>

<script>

import axios from 'axios';

export default {
    name: 'news',
  data: () => ({
	news: [],
	errors: []
  }),
created () {
	axios.get('https://min-api.cryptocompare.com/data/v2/news/?lang=EN')
	  .then(response => {
		this.news = response.data.Data
		console.log(response.data.Message) // This will give you access to the full object
	  })
	  .catch(e => {
		this.errors.push(e)
	  })
  }
  }
  

</script>

<style>
 .card {
        margin: 0 auto; /* Added */
        float: none; /* Added */
        margin-bottom: 10px; /* Added */
        text-align: left;
}
.btn-primary
{
background-color: #4CAF50;
}



</style>