<template>
  <header>
      <router-link to="/">
        <h1>VueFlix</h1>
      </router-link>
  </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style lang="scss" scoped>    
  h1{
     color: #e50914;
  }

  header{
    // @media (min-width: 768px ) {
    //   justify-content: left;
    //   align-items: left;
    // }
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 10px 16px;
  }

</style>