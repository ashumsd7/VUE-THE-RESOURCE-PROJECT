<template>
  <ul>
    <learning-resource 
    :key="res.id" v-for="res in resources"
    id="res.id"
    :title="res.title"
    :description="res.description"
    :link="res.link"
    >
    </learning-resource>
  </ul>
</template>

<script>
import LearningResource from   './LearningResource'
export default {
    components:{LearningResource},
    inject:['resources']
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>