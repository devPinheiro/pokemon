<template>
  <div >
    <h1>This is the page for the pokermon cards</h1>
    <button class="" @click="logOut">Logout</button>
  </div>
</template>

<script>
  export default {
    methods: {
      logOut () {
        if(localStorage.getItem('pokermonUser')){
           localStorage.setItem('pokermonUser', null);
           this.$router.push('/');
        }
      }
    }
  }
</script>

<style scoped>

</style>
