<template>
  <div class="app">
    <Header />
  </div>
  <router-view />
</template>

<script>
  import Header from './components/Header'
export default {
  components: {
    Header
  }
}
</script>


<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500;1,700&display=swap');

  *{
    margin:0; 
    padding: 0;
    box-sizing: border-box;
    font-family: 'Roboto', sans-serif;
  }

  body{
    background-color: #141414;
    color: #FFF;
  }
  
  a{
    text-decoration: none;
  }

  header{
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 10px 16px;
  }

  h1{
    color: #e50914;
  }

</style>
