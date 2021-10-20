<template>
<div>
<h1>{{ msg }}</h1>

</div>
   <section class="section">
 <table class="table table-striped">
  <thead>
   <tr class="is-selected">
     <th>#</th>
     <th>Name</th>
     <th>Market Cap</th>
     <th>Price</th>
     <th>Volume (24h)</th>
     <th>Circulating Supply</th>
     <th>Open (24h)</th>
   </tr>
  </thead>
  <tfoot>
   <tr>
     <th>#</th>
     <th>Name</th>
     <th>Market Cap</th>
     <th>Price</th>
     <th>Volume (24h)</th>
     <th>Circulating Supply</th>
     <th>Open (24h)</th>
   </tr>
  </tfoot>
  <tbody>
   <tr v-for="(value, key, index) in coins" v-bind:key="(value, key, index)">
     <th>{{index+1}}</th>
     <td>{{key}}</td>
     <td>{{value.USD.MKTCAP}}</td>
     <td>{{value.USD.PRICE}}</td>
     <td>{{value.USD.VOLUME24HOUR}}</td>
     <td>{{value.USD.SUPPLY}}</td>
     <td>{{value.USD.OPEN24HOUR}}</td>
   </tr>
  </tbody>
 </table>
  </section>
  <div>
    <button class="btn btn-primary" v-on:click="reloadPage">Osvjezi</button>
  
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'helloworld',
  props: {
    msg: String
  },
  data: () => ({
    coins: [],
    errors: []
  }),
  
  created () {
   
      axios.get('https://min-api.cryptocompare.com/data/pricemultifull?fsyms=BTC,ETH,DOGE,USDT,DASH&tsyms=USD,EUR')
      .then(response => {
       this.coins = response.data.DISPLAY
        console.log(response)
      })
      .catch(e => {
        this.errors.push(e)
      })
      
      
  },
  methods: {
  reloadPage(){
    window.location.reload()
  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.btn-primary
{
background-color: #4CAF50;
}
</style>
