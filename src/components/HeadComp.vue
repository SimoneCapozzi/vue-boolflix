<template>
  <header>
    <div>
      <h1>Boolflix</h1>
    </div>

    <div>
      <input
        v-model.trim="textToSearch"
        placeholder="Cerca film o serie tv"
        class=""
        type="text"
        @keyup.enter="$emit('startSearch', { text: textToSearch, type: 'all' })"
      />

      <button
       @click="$emit('startSearch',{text:textToSearch, type:'movie'})"
       class="ms-3">Cerca Film</button>

      <button
      @click="$emit('startSearch', { text: textToSearch, type: 'tv' })"
      class="ms-3 me-3">Cerca serie tv</button>
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

header{
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 70px;
  background-color: black ;
  border-bottom: 3px solid red;
}

h1{
  margin-left: 10px;
  color: red;
}

input{
 outline:none;
 background-color: white;
}

button {
  background-color: red;
  border: none;
  color: black;
  border-radius: 5px;
  padding: 5px;
  &:hover {
    color: red;
    background-color: black;
    border: 1px solid red;
    border-radius: 5px;
  }
} 






</style>
