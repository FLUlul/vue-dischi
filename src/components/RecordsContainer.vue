<template>
  <div id="container">

    <main @onload="$emit('loadIt', filteredArray)">

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

export default {
  name: 'RecordsContainer',
  components: {
    Record,
  },
    props: {
      savedValue: String,
  },
  
  data() {
    return{
      records: [],
      filteredArray: [],
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
        return item.genre.toLowerCase().includes(this.savedValue.toLowerCase()) /* || item.author.toLowerCase().includes(this.savedValue.toLowerCase()) */
      })
    },
    filteredArrayFun() {
      
      this.records.forEach((element) => {
        if(!this.filteredArray.includes(element.genre)){
          this.filteredArray.push(element.genre)
        }
      })
      return this.filteredArray
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  main{
    background-color: #1e2d3b;
    padding: 30px;
    text-align: center;
    color: white;

    span{
      margin-left: 20px;
    }

    .loading{
      text-align: center;
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
