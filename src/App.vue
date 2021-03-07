<template>
  <div id="app">
    <div>
      <b-navbar toggleable="lg" type="dark" variant="info">
        <router-link to="/">Home</router-link>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <b-navbar-nav class="ml-auto">
        <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search" @click="Search()"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
          </b-nav-form>
        </b-navbar-nav>
        </b-navbar>
   
    </div>
    <router-view/>
  </div>
</template>
<script>
import axios from 'axios';
export default{
  methods: {
    Search(){
      const router = this.$router;
      for(let i =0; i<=this.toonList.mange.length; i++){
        if(this.ss == this.toonList.mange[i].title){
          alert(this.toonList.mange[i].title);
          router.push({ 
            path: `/About/${this.toonList.mange[i].mal_id}`
          });
          break;
        }else if (99 == i){
          router.push({
            path: `/`
          });
        }
      }
    }
  },
  data() {
    return {
      ss: "",
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
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}
#nav a {
  font-weight: bold;
  color: #2c3e50;
}
#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
