<template>
  <main class="container">
    <div>
      <h1>{{ titles[type] }}</h1>
    </div>

    <div class="copertina">
      <CardFilm
        v-for="card in list"
        :key="card.id"
        :card="card"
      />
    </div>

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

.copertina{
  display: inline-flex;
}

</style>