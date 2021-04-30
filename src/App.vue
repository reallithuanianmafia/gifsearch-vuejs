<template>
  <div id="app">
      <div class="container">
        <div class="row">
          <div class="col-md-5 offset-md-4">
          <img src="./assets/logo.png" class="logo">
          </div>
        </div>
      </div>
      <Search v-on:SearchRequested="handleSearch"></Search>
      <Preview v-bind:gifs="gifs" />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import Search from './components/Search';
import Preview from './components/Preview';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Preview,
    Search
  },
  created()
  {
    this.fetchData();
  },
  data()
  {
    return{
      gifs: [],
    }
  },
  methods: {
      fetchData()
      {
        console.log('Started fetching data');
        axios.get('https://api.giphy.com/v1/gifs/trending?api_key=YOUR_API_KEY_GOES_HERE')
        .then((res)=> {this.pushItems(res.data.data)} )
        .catch((err)=> {console.log('got error')} );
      },
      pushItems(arr)
      {
        this.gifs = arr;
      },
      handleSearch(value)
      {
        console.log(value);
        this.gifs = [];
        var theurl = 'https://api.giphy.com/v1/gifs/search?api_key=YOUR_API_KEY_GOES_HERE&q='+value+'&limit=100&offset=0&rating=g&lang=en';
        console.log(theurl);
        axios.get(theurl)
        .then((res) => { this.pushItems(res.data.data) })
        .catch((err) => { console.log('got error') });
      }
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  
}
.logo {
  margin: 5% 1%;
  text-align: center;
}
body {
    min-height: 100%;
  min-width: 100%;
  background: black;
}
</style>
