<template>
  
  <v-row>
      <v-col v-for="(item, index) in users" :key="index">{{item.title}}</v-col>
  </v-row>
      
     
</template>
      
   
<script>
const axios = require('axios')
let url = 'https://liber.liber-develop.com/wp-json/wp/v2/posts/?per_page=3'

export default {
 
  async asyncData({ params, error, payload }) {
    if (payload) {     
      return { users: payload }
    }else{
       return axios.get(url).then((res) => {
        return { users: res.data }
      })
    }
  }
}
</script>

     