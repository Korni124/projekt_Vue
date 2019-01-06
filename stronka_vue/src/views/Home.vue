<template>
  <div class="wrapper">
    <div class="search">
      <label for="Search">Search</label>
      <input id="search" name="Search" v-model="searchValue" @input="handleInput"/>
      <ul>
        <li v-for= "item in results" :key="item.data[0].nasa.id">
          <p>{{item.data[0].description}}</p>

        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
const API='https://images-api.nasa.gov/search/search';

export default {
  name: 'Search',
  data(){
    return {
      searchValue: '',
      resulte:[],
    };
  },
  methods:{
    handleInput:debounce(function(){
      axios.get('${API}?q=${this.searchValue}&media_type=image')
        .then((response)=>{
          this.results=response.data.collection.items;
        })
        .catch((error)=>{
          console.log(error);
        });
    },500),
      
  },
  
};
</script>
<style lang="scss" scoped>
  .wrapper{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin:0;
    padding: 30px;
    width:100%;
  }
  .search{
    display: flex;
    flex-direction: column;
    width: 260px;

    label{
      font-family: Montserrot, sane-serif;
    }

    input{
      height: 30px;
      border: 0;
      border-bottom: 1px solid block;
    }
  }  

</style>

