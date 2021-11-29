<template>
  <div id="container">
    <header>
      <img src="../assets/spotify-logo.png" alt="logo spotify">
    </header>

    <main>

      <SelectGenre @changeIt="selectedValue"/>


      <div class="loading" v-if="records.length === 0">... Loading ...</div>

      <div id="container-records" v-else>

        <Record
        v-for="record, i in filteredRecords"
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
import SelectGenre from '@/components/SelectGenre.vue'

export default {
  name: 'RecordsContainer',
  components: {
    Record,
    SelectGenre,
  },
  
  data() {
    return{
      records: [],
      savedValue: "",
    }
  },

  created(){
    axios
    .get("https://flynn.boolean.careers/exercises/api/array/music")
    .then((result) =>  {
        this.records = result.data.response;
        /* console.log(this.records); */
    })
    .catch((error) => {
      console.log(error);
    })
  },

  computed: {
    filteredRecords() {
      if (this.savedValue === "All"){
        return this.records
      } 
      return this.records.filter((item) => {
        return item.genre.toLowerCase().includes(this.savedValue.toLowerCase())
      })
    }
  },

  methods:{
    selectedValue(valueImport){
      this.savedValue = valueImport;
      console.log(this.savedValue);
    }
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
    text-align: center;

    .loading{
      text-align: center;
      color: white;
      font-size: 50px;
    }
  }

  #container-records {
    width: 70%;
    margin: 10px auto;
    display: flex;
    flex-wrap: wrap;
  }
</style>
