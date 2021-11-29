<template>
  <select v-model="valueOpz" @change="$emit('changeIt', valueOpz)">
    <option value="'All'">All</option>
    <option value="'Rock'">Rock</option>
    <option value="'Pop'">Pop</option>
    <option value="'Jazz'">Jazz</option>
    <option value="'Metal'">Metal</option>
  </select>
</template>

<script>
export default {
  name: 'SelectGenre',
  data(){
    return {
      valueOpz: "All",
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
