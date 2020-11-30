<template>
  <BaseCard>
    <BaseButton @click="setSelectedTab('stored-resources')" :mode="storedResBtn"
      >Stored Resources</BaseButton
    >
    <BaseButton @click="setSelectedTab('add-resource')" :mode="addResBtn"
      >Add Resource</BaseButton
    >
  </BaseCard>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation.',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn with google.',
          link: 'https://google.com'
        }
      ]
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      removeResource: this.removeResource
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title,
        description,
        link: url
      };

      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
    removeResource(resId) {
      const resIndex = this.storedResources.findIndex(res => (res.id = resId));
      this.storedResources.splice(resIndex, 1);
    }
  },
  computed: {
    storedResBtn() {
      return this.selectedTab === 'stored-resources' && 'flat';
    },
    addResBtn() {
      return this.selectedTab === 'add-resource' && 'flat';
    }
  }
};
</script>

<style>
</style>