<template>
  <div id="app">
    <input type="text" v-model="getText">
    <button @click="showAdress" type="submit">変換 </button>
    <Header :parentText="getText"> </Header>
     <p>住所：{{show}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data(){
    return{
      show:""
    };
  },
  props:["getText"],
   method:{
     async showAdress(){
      let item = await axios.get('https://apis.postcode-jp.com/api/v3/postcodes/${getText}?Alladress');
      this.show = item.data;
    }
  },
};
</script>