<template>
  <div id="container">
    <header>
      <img src="../assets/spotify-logo.png" alt="logo spotify">
    </header>

    <main>

      <div id="container-records">

        <Record
        v-for="record, i in records"
        :key="i"
        :details="record"
        /> 

      </div>

    </main>

  </div>
</template>

<script>
import axios from 'axios'
import Record from '@/components/Record.vue'

export default {
  name: 'RecordsContainer',
  components: {
    Record,
  },
  
  data() {
    return{
      records: [],
    }
  },

  created(){
    axios
    .get("https://flynn.boolean.careers/exercises/api/array/music")
    .then((result) =>  {
        this.records = result.data.response;
    })
    .catch((error) => {
      console.log(error);
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  header{
    background-color: #2e3a46;
    padding: 10px 20px;

    img{
      width: 50px;
    }
  }
  main{
    background-color: #1e2d3b;
    padding: 30px;
  }

  #container-records {
    width: 70%;
    margin: 10px auto;
    display: flex;
    flex-wrap: wrap;
  }
</style>
