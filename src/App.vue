<template>
  <div id="app">
    <header>
      
      <img src="./assets/spotify-logo.png" alt="logo spotify">

      <div>
        <span>Select Genre: </span>
        <SelectGenre 
        @changeIt="getSelectedValue"
        :arrayDetails="savedFilteredArr"
        />

        <!-- <span>Select Artist: </span>
        <SelectArtist 
        @changeIt="selectedValue"
        :arrayDetails="records"
        /> -->
      </div>

    </header>

    <RecordsContainer
    @loadIt="getFilteredArray"
    :savedValue="savedValueOut"
    />

  </div>
</template>

<script>
import RecordsContainer from './components/RecordsContainer.vue'
import SelectGenre from '@/components/SelectGenre.vue'
/* import SelectArtist from '@/components/SelectArtist.vue' */

export default {
  name: 'App',
  components: {
    RecordsContainer,
    SelectGenre,
    /* SelectArtist, */
  },
  data() {
    return{
      savedValueOut: "",
      savedFilteredArr: [],
    }
  },
  methods:{
    getSelectedValue(valueImport){
      this.savedValue = valueImport;
      console.log(this.savedValue);
    },
    getFilteredArray(filteredArray){
      this.savedFilteredArr = filteredArray;
      console.log(this.savedFilteredArr);
    }
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #2e3a46;
  height: 100vh;
}
header{
  background-color: #2e3a46;
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;

  img{
    width: 50px;
  }
}
</style>
