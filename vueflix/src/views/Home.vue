<template>
  <main class="home">
    <div class="featured-card">
      <router-link to="'/movie/'+imdbID">
        <img src="https://sm.ign.com/t/ign_br/screenshot/default/narutinho_rq9u.1280.jpg" alt="item image" class="featured-img">
        <div class="detail">
          <h2>Naruto</h2>
          <p>
Naruto é uma série de mangá escrita e ilustrada por Masashi Kishimoto, que conta a história de Naruto Uzumaki, um jovem ninja que constantemente procura por reconhecimento e sonha em se tornar Hokage, o ninja líder de sua vila.</p>
        </div>
      </router-link> 
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
      position: relative;

      .featured-img {
        display: block;
        width: 100%;
        height: 300px;
        object-fit: cover;

        position: relative;
        z-index: 0;
      }

      .detail{
        position: absolute;
        left: 0;
        right: 0;
        bottom: 0;
        background-color: rgba(0, 0, 0, 0.6);
        padding: 16px;
        z-index: 1;


        h2{
          margin-bottom: 16px;
        }
      }
    }
  }
</style>
