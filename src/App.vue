<template>
  <TheHeader title="RememberMe" />
  <TheResources />
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/learning-resources/TheResourse';
export default {
  components: {
    TheHeader,
    TheResources
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Comfortaa:400,500,700');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Comfortaa', sans-serif;
}

body {
  margin: 0;
}
</style>