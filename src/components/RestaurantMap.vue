<template>
  <div>
    <GmapMap
  :center="{lat:item[1], lng:item[0]}"
  :zoom="7"
  map-type-id="terrain"
  style="width: 500px; height: 300px"
>
</GmapMap>


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
