<template>
  <main class="container">
    <h1>{{ titles[type] }}</h1>
    <CardFilm
      v-for="card in list"
      :key="card.id"
      :card="card"
     />
  </main>
</template>

<script>
import CardFilm from '@/components/CardFilm';
export default {
  name: 'MainComp',
  components:{
    CardFilm
  },
  props:{
    type: String,
    list: Array
  },
  data(){
    return{
      titles:{
        'movie': 'Film trovati',
        'tv': 'Serie tv trovate'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
</style>