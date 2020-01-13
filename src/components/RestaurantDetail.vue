<template>
  <div>
    <h1 class="titre">Details du restaurant {{nom}}</h1>
    <p> Type : {{cuisine}} </p>
    <p> Adresse : {{addr}} </p>

    <restaurant-carte :item="carte"></restaurant-carte>
    <restaurant-menu :item="menus"></restaurant-menu>
    <restaurant-note :item="note"></restaurant-note>
    <restaurant-map :item="coord"></restaurant-map>

  </div>
</template>

<script>
import RestaurantCarte from './RestaurantCarte';
import RestaurantMenu from './RestaurantMenu';
import RestaurantNote from './RestaurantNote';
import RestaurantMap from './RestaurantMap';
export default {
  name: "RestaurantDetail",
  props: {},
  components: {
    RestaurantCarte,
    RestaurantMenu,
    RestaurantNote,
    RestaurantMap
  },
  computed: {
    id() {
      return this.$route.params.id
    }
  },
  data:() => {
    return {
      restaurant: {},
      nom: "",
      cuisine: "",
      carte: [],
      menu: [],
      coord: [],
      note:[],
      addr: "",
      lon: "",
      lat: "",
      quartier: "",
      apiURL: "http://localhost:8080/api/restaurants"
    };
  },
  mounted() {
    console.log("AVANT AFFICHAGE !");
    console.log("On va chercher les détails du restaurant id = " + this.$route.params.id)
    console.log("ID = " + this.id);
    this.getDataFromServer();
  },
  methods: {
    async getDataFromServer() {
      
        let url = this.apiURL + "/" + this.id;

        try {
          let reponseJSON = await fetch(url, {
            method: "GET"
          });
          let reponseJS = await reponseJSON.json();
          this.restaurant = reponseJS.restaurant;
          this.nom = reponseJS.restaurant.name;
          this.cuisine = reponseJS.restaurant.cuisine;
          this.addr = reponseJS.restaurant.address.building + " " + reponseJS.restaurant.address.street + ", " + reponseJS.restaurant.address.zipcode + " " + reponseJS.restaurant.borough;
          this.carte = reponseJS.restaurant.carte;
          this.menus = reponseJS.restaurant.menus;
          this.evaluations = reponseJS.restaurant.grades;
          this.coord = reponseJS.restaurant.address.coord;
        } catch (err) {
          console.log("Erreur dans les fetchs GET " + err.msg);
        }
    },
    
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.titre{
  
}
</style>
