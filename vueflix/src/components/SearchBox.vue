<template>
  <div class="search">
      <form @submit.prevent="SearchMovies" class="search-box" >
          <input type="text" placeholder="Filmes, séries ou Animes." v-model="search">
          <input type="submit" value="Buscar">
      </form>

      <div class="movies-list">Movies</div>
  </div>
</template>

<script>

import { ref } from 'vue';
import env from '../env'

export default {
    name: "SearchBox",
    
    setup() {
        const search = ref("");
        const movies = ref ([]);

        const SearchMovies = () => {
            if (search.value != ""){
                fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
                    .then(response => response.json())
                    .then(data => {
                        console.log(data);  
                    });
            }
        }

        return{ 
            search,         
            movies,
            SearchMovies
        }
    }
}
</script>

<style lang="scss" scoped>
    .search-box {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 16px;
    

        input {
            display: block;
            border: none;       
            outline: none;   
            border-radius: 8px;
            font-size: 20px;

            &[type="text"] {
                width: 100%;
                background-color: #496583;
                padding: 10px 16px;
                margin-bottom: 15px;
                transition: 0.4s;
                
                    

                &::placeholder {
                    color: #f3f3f3;
                }

            }

            &[type="submit"] {
                width: 100%;
                max-width: 300px;
                padding: 16px;
                background-color: #e50914;
                text-transform: uppercase;
                font-weight: bold;

                &:active {
                    opacity : 0.5;
                }
            }
        }   
    }

</style>