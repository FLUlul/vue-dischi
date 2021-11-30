<template>
  <select v-model="valueOpz" @change="$emit('changeIt', valueOpz)">
    <option :value="'All'">All</option>
    <option v-for="objDetails, i in arrayData" :key="i" :value="objDetails.author">{{ objDetails.author }}</option>
  </select>
</template>

<script>
export default {
  name: 'SelectArtist',
  data(){
    return {
      valueOpz: "All",
    }
    
  },
  props: {
    arrayData: Array,
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
