<template>
  <main class="home">
    <div class="featured-card">
      
        <img src="https://pbs.twimg.com/media/ErZmmEpXMAAKqWu?format=jpg&name=medium" alt="item image" class="featured-img">

       
    </div>

    <SearchBox />
  </main>
</template>

<script>

import SearchBox from '../components/SearchBox'

export default {
  components: {
     SearchBox
  }
}
</script>

<style lang="scss" scoped>
  .home{
      

    .featured-card {
      @media (min-width: 768px ) {
        display: block;

      }
      display: none;
      position: relative;

      .featured-img {
        display: block;
        width: 100%;
        height: 350px;
        object-fit: cover;


      }
    }
  }
</style>
