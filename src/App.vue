<template>
  <div id="app">
    
    
    <!-- invoco la funzione all'evento $emit startSearch -->
    <HeadComp @startSearch="startSearch" />

    <!-- se non ho risultati visualizzo h1 -->
    <h1 v-if="results.movie.length === 0 && results.tv.length === 0">Nessun risultato trovato</h1>


    <!-- ho 2 componenti Main per movie e tv e li visualizzo solo se coi sono elementi nell'array -->
    <!-- passo 2 pros: tipo di dato (movie o tv) l'elenco dei risultati -->
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
    /* avvio la ricerca */
    startSearch(obj){
      /* cancello le ricerche passate */
      this.resetResults();
      /* se cerca sia film che tv faccio 2 chiamate */
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

    /* funzione per la chiamata axios */
    getAPI(query, type){
      
      /* effettuo la chiamata solo se c'è un testo */
      if(query !== ''){
        axios.get(this.apiUrl+type,{
            params:{
              api_key: this.apiKey,
              query: query,
              language: 'it-IT'
            }
          })
          .then(res => {
            /* in base alla ricerca salvo il dato nell'array corrispondente */
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
  @import './assets/style/general';
#app {
  
  text-align: center;
  color: #2c3e50;
  
}



</style>