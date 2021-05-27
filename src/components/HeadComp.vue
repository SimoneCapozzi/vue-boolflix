<template>
  <header>

    <div class="container d-flex pt-3">
      <div class="flex-grow-1">
          <input 
          v-model.trim="textToSearch"
          placeholder="Cerca film o serie tv"
          class="form-control"
          type="text" />
      </div>
      <div>
        <button 
        @click="$emit('startSearch',{text:textToSearch, type:'movie'})"
        class="btn btn-primary ms-3">CERCA FILM</button>
      </div>
      <div>
        <button 
        @click="$emit('startSearch',{text:textToSearch, type:'tv'})"
        class="btn btn-primary ms-3">CERCA SERIE</button>
      </div>
      <div>
        <button 
        @click="$emit('startSearch',{text:textToSearch, type:'all'})"
        class="btn btn-primary ms-3">CERCA TUTTO</button>
      </div>

    </div>

  </header>
</template>

<script>
export default {
  name: 'HaedComp',
  data(){
    return{
      textToSearch: ''
    }
  }
}
</script>

<style lang="scss" scoped>
header{
  display: flex;
  height: 70px;
  background-color:black;

}
button{
  background-color: red;
  border-color: red;
  color: black;
  &:hover{
    color:red;
    background-color: black;
    border-color: red;
  }
}


</style> 