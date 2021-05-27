<template>
  <div id="app">
    
    

    <HeadComp @startSearch="startSearch" />

    <h1 v-if="results.movie.length === 0 && results.tv.length === 0">Nessun risultato trovato</h1>
 
    <MainComp v-if="results.movie.length > 0"  type='movie' :list="results.movie" />
    <MainComp v-if="results.tv.length > 0" type='tv' :list="results.tv"/>

  

  </div>
</template>

<script>
  
  import HeadComp from './components/HeadComp';
  import MainComp from './components/MainComp';
  import axios from 'axios';


export default {
  name: 'App',
  components: {
    
    HeadComp,
    MainComp,
    
  },
  data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiKey: '3dac2be19bef3c8074c204f48bb3f900',
      results:{
        'movie':[],
        'tv':[]
      }
    }
  },
  methods:{
    startSearch(obj){
      this.resetResults();
      if(obj.type === 'all'){
        this.getAPI(obj.text, 'movie');
        this.getAPI(obj.text, 'tv');
      }else{
        this.getAPI(obj.text, obj.type);
      }
    },
    resetResults(){
      this.results.movie = [];
      this.results.tv = [];
    },
    getAPI(query, type){
      
      if(query !== ''){
        axios.get(this.apiUrl+type,{
            params:{
              api_key: this.apiKey,
              query: query,
              language: 'it-IT'
            }
          })
          .then(res => {
            this.results[type] = res.data.results;
            console.log('MOVIE',this.results.movie);
            console.log('TV', this.results.tv);
          })
          .catch(err => {
            console.log(err);
          })
      }
    }
  },
  created(){
  }
}
</script>

<style lang="scss">
#app {
  
  text-align: center;
  color: #2c3e50;
  
}
@import './assets/style/general';
</style>