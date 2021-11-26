<template>
    <div class="record-card">
        <img :src="details.poster" :alt="details.author">

        <h2>{{ details.title }}</h2>

        <div>{{ details.author }}</div>

        <div>{{ details.year }}</div>

    </div>
</template>

<script>
export default {
  name: 'Record',
  props: {
      details: Object,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .record-card{
        width: calc(100% / 5 - 40px);
        text-align: center;
        padding: 20px;
        margin: 10px 20px;
        background-color: #2e3a46;

        img{
            max-width: 100%;
            max-height: 200px;
        }

        h2{
            color: white;
            margin: 20px;
        }

        div{
            color: grey;
        }
    }
</style>
