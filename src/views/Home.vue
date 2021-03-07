<template>
  <div class="home">
<div class="row">
    
  <HelloWorld v-for="(item,index) in toonList.manga" :key="index"
   :name="item.title" 
    :img="item.image_url"
    :id="item.mal_id"
  />
  
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import axios from 'axios'
export default {
  name: "Home",
  components: {
    HelloWorld,
  },
  data() {
    return {
      toonList: "",
      url: "https://api.jikan.moe/v3/magazine/1/1",
    };
  },
  
  mounted() {
    axios
      .get(this.url)
      .then((response) => {
        this.toonList = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>