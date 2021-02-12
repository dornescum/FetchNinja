<template>
<!--  dc este adevarta altfel-->
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <p>{{ job.details }}</p>
  </div>
  <div v-else>
    <p>Loading job details...</p>
  </div>
</template>

<script>
export default {
  // id props si il pot folosi
  props: ['id'],
  data() {
    return {
      // initial este null si de asta il pun in v-if
      job: null
    }
  },
  mounted() {
    fetch('http://localhost:3000/jobs/' + this.id)
        .then(res => res.json())
        .then(data => this.job = data)
        .catch(err => console.log(err.message))
  }
}
</script>

<style>
</style>