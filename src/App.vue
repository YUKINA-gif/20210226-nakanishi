<template>
  <div id="app">
    <input type="text" v-model="postalCode"/>
    <button @click="userClick">住所自動入力</button>
    <p>Address : {{ address }}</p>
    <router-view/>
  </div>
</template>


<script>
import axios from 'axios';
export default {
  data() {
    return {
      postalCode:"",
      address:"",
    }
  },
  methods:{
  async userClick(){
    const item = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.postalCode}?apiKey=83IMiq6S0eYbQbMYIaN4iel7etb1PrzaYQBd2qN`);
  
  this.address = item.data[0].allAddress;
  }
}
};
</script>


<style>
</style>