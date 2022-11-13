<template>
  <div class="about">
    <div class="container">
    <label for="search">Search label </label>
  <input 
  type="text" 
  name="search" 
  id="search" 
  v-model="searchValue"
  @input="handleInput"
  >
</div>  
<ul>
<li><p v-for="item in results" :key="item.data[0].nasa_id">{{ searchValue != "" ? item.data[0].title : ""}}</p></li>
</ul>
</div>

</template>

<script>
import axios  from "axios";
import debounce from "lodash.debounce"

const Api = 'https://images-api.nasa.gov'
export default {
  name: "Search",
data() {
return {
  searchValue: '',
  results: []
}
},
methods: {
  handleInput: debounce(function() {
    axios.get(`${Api}/search?q=${this.searchValue}&media_type=image`)
    .then((response) => {
      console.log(response.data.collection.items);
      this.results = response.data.collection.items;
    })
    .catch((error) => {
      console.log(error)
    });
    console.log(this.searchValue)
  }, 500)
}
}
</script>
<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }

  .about ul {
    list-style: none;
  }
}
</style>
