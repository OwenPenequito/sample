<template>
  <div class="Details">
  <div v-if="Article">
    <h1>{{ Article.title }}</h1>
    <p>{{ Article.details }}</p>
  </div>
  </div>
</template>

<script>
export default {
    props: ['id'],
    data() {
        return {
            Article: null
        }
    },
    mounted() {
        fetch('http://localhost:3000/Articles/' + this.id)
        .then(res => res.json())
        .then(data => this.Article = data)
        .catch(err => console.log(err.message))
    }
}
</script>

<style>

.Details {
  height: 850px;
  width: 1450px;
  background: #ffffff;
  padding: 25px;
  position: relative;
  top: -10px;
  left: -10px;
}

</style>