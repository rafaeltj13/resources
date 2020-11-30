<template>
  <ul>
    <LearningResource
      v-for:="res in resources"
      :key="res.id"
      :title="res.title"
      :description="res.description"
      :link="res / link"
      @delete-resource="removeResource"
    ></LearningResource>
  </ul>
</template>

<script>
import LearningResource from './LearningResource';
export default {
  name: 'StoredResources',
  components: {
    LearningResource
  },
  inject: ['resources', 'removeResource']
};
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