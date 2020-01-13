<template>
  <div>
    <h1>Details du restaurant {{nom}}</h1>
    <p> Type : {{cuisine}} </p>
    <p> Adresse : {{addr}} </p>
  </div>
</template>

<script>
export default {
  name: "RestaurantDetail",
  props: {},
  components: {
  },
  computed: { // computed data, permet de définir des data "calculées"
    id() {
      // on y accèdera par {{id}} dans le template, et par this.id
      // dans le code
      return this.$route.params.id
    }
  },
  data:() => {
    return {
      restaurant: {},
      nom: "",
      cuisine: "",
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
        } catch (err) {
          console.log("Erreur dans les fetchs GET " + err.msg);
        }
    },
    
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
