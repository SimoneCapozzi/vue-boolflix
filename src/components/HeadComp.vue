<template>
  <header class="d-flex">
    <div>
      <h1 class="ms-3">Boolflix</h1>
    </div>
    <div class="search d-flex align-items-center">
      <input
        v-model.trim="textToSearch"
        placeholder="Cerca film o serie tv"
        class="form-control"
        type="text"
        @keyup.enter="$emit('startSearch', { text: textToSearch, type: 'all' })"
      />
      <div>
        <button
          @click="$emit('startSearch', { text: textToSearch, type: 'movie' })"
          class=" ms-3"
        >
          CERCA FILM
        </button>
      </div>
      <div>
        <button
          @click="$emit('startSearch', { text: textToSearch, type: 'tv' })"
          class=" ms-3 me-3"
        >
          CERCA SERIE
        </button>
      </div>
      <!-- <div>
          <button 
          @click="$emit('startSearch',{text:textToSearch, type:'all'})"
          class="btn btn-primary ms-3">CERCA TUTTO</button>
        </div> -->
    </div>
  </header>
</template>

<script>
export default {
  name: "HaedComp",
  data() {
    return {
      textToSearch: "",
    };
  },
};
</script>

<style lang="scss" scoped>
header {
  display: flex;
  justify-content: space-between;
  height: 70px;
  background-color: black;
}

h1{
  margin-top: 10px;
  color: red;
}

button {
  background-color: red;
  border-color: red;
  color: black;
  border-radius: 5px;
  padding: 5px;
  &:hover {
    color: red;
    background-color: black;
    border-color: red;
    border-radius: 5px;
  }
}
</style>
