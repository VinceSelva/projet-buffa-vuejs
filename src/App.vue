<template>
  <div id="app">
    <div class="accMenu">
      <router-link to="/">Accueil</router-link>
    </div>

    <div class="restMenu">
      <router-link to="/restaurants">Les restaurants</router-link>
    </div>
       <router-view></router-view>
    <!--<div class="imgAcc">
      <img src="../src/assets/fond_accueil.png">
    </div>-->
  </div>
</template>

<script>

export default {
  name: "app",
  components: {
  },
  data: function() {
    return {
      nom: "buffa"
    };
  },
  mounted()  {
    console.log("avant affichage");
  }
};
</script>

<style>

*{
  font-family: Lucida Sans Unicode;
}

.accMenu,
.restMenu{
  margin-bottom: 100px;
  text-transform: uppercase;
  text-decoration: none;
  font-size: 30px;
  background-color: grey;
  padding: 30px;
  border-radius: 5px;
}


.accMenu{
  margin-left: 30px;
  float: left;
}

.restMenu{
  margin-right: 30px;
  float: right;
}

.imgAcc{
  width: auto !important;
  height: 10px !important;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
