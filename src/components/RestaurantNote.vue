<template>
  <div>
    <h1> Avis </h1>
    <div v-if="hasEval">
      <div v-for="note in item" :key="note.date"> 
        <p> Date : {{note.date}}</p>
        <p> Grade : {{note.grade}}</p>
        <p> Note : {{note.score}}</p>
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
      evaluations: this.value,
      hasEval: true
    }
  },
  updated(){
    this.hasEval = this.verifNote();
  },
  methods: {
    verifNote(){
      if(this.item.length > 0){
        return true;
      } else {
        return false;
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
