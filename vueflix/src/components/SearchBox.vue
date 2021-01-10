<template>
  <div class="search">
      <form @submit.prevent="SearchMovies()" class="search-box" >
          <input type="text" placeholder="Filmes, séries ou Animes." v-model="search">
          <input type="submit" value="Buscar">
      </form>

        <div class="movies-list">
            <div class="movie" v-for="movie in movies" :key="movie.imdbID">
                <router-link :to="'/movie/'+ movie.imdbID" class="movie-link">
                    <div class="product-image">
                        <img :src="movie.Poster" alt="Movie Poster">
                        <div class="type">{{ movie.Type }}</div>
                    </div>
                    <div class="detail">
                        <p>{{  movie.Year  }}</p>
                        <h3>{{ movie.Title }}</h3>
                    </div>
                </router-link>
         </div>
      </div>
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
                        movies.value = data.Search;
                        search.value = "";
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
    // search box
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

    // movies list
    .movies-list{
        display: flex;
        flex-wrap: wrap;
        margin: 0px 8px ;

        .movie {
            @media (min-width: 768px ) {
                flex: 50%;
            }
            max-width: 100%;
            flex: 100%;
            padding: 16px 8px;

            .movie-link{
                display: flex;
                flex-direction: column;
                height: 100%;

                .product-image {
                    position: relative; 
                    display: block;

                    img{
                        display: block;
                        width: 100%;
                        height: 275px;
                        object-fit: cover;
                    }

                    .type{
                        position: absolute; 
                        padding: 8px 16px;
                        bottom: 16px; 
                        left: 0px;
                        text-transform: capitalize;
                        background-color:  #e50914;
                        font-weight: bold;  

                    }
                }

                .detail{
                    @media (min-width: 768px ) {}
                    padding: 16px 8px;
                    flex: 1 1 100%;
                    border-radius: 0px 0px 0px 8px;
                    background-color: #496583;
                }
            }
        }

        
    }

</style>