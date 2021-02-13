<template>
  <div id="app">
    <input type="text" v-model="getText">
    <button @click="showAdress" type="submit">変換 </button>
     <p>住所：{{show}}</p>
  </div>
</template>

<script>
import axios from "axios";
 let getText;
export default {
  
  data(){
    return{
      show:"",
      getText:""
    };
  },
   methods:{
     async showAdress(){
      let item = await axios.get(`https://apis.postcode-jp.com/api/v3/postcodes/postcode=${getText}?apikey=fabCn3nwAAosqqjhmKDAC5fhlZKgNh6fPvWwBZY`);
      this.show = item.allAddress;
    }
  },
};
</script>