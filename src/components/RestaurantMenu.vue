<template>
  <div>
    <h1> Le menu </h1>
    <div v-if="item">
      <div v-for="menu in item" :key="menu.nom">
        <h2>{{menu.nom}}</h2>
        <p> Le prix : {{menu.prix}} €</p>
        <!-- <button v-on:click="afficheMenu()">Le menu</button> -->
        <h3> Les entrées : </h3>
        <p v-for="entree in menu.entrees" :key="entree"> {{entree}}</p>
        <h3> Les plats : </h3>
        <p v-for="plat in menu.plats" :key="plat"> {{plat}}</p>
        <h3> Les desserts : </h3>
        <p v-for="dessert in menu.desserts" :key="dessert"> {{dessert}}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
  item: Array
  },

  data: function(){
    return {
    }
  },
  mounted(){
    
  },
  methods: {
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
