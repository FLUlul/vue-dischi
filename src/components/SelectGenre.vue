<template>
  <select v-model="valueOpz" @change="$emit('changeIt', valueOpz)">
    <option :value="'All'">All</option>
    <option v-for="objDetails, i in arrayDetails" :key="i" :value="objDetails">{{ objDetails }}</option>
  </select>
</template>

<script>
export default {
  name: 'SelectGenre',
  data(){
    return {
      valueOpz: "All",
    }
    
  },
  props: {
      arrayDetails: Array,
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
