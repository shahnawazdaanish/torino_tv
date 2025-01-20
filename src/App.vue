<template>
  <v-app full-height>
    <router-view/>
  </v-app>
  <StarFall/>
</template>

<script lang="ts">
import StarFall from './components/StarFall.vue';

export default {
  name: "App",
  components: {StarFall},
};
</script>
<style>

.v-application {
  font-family: "Lobster", serif;
  margin: 0;
  padding: 0;
  height: 100%;
  overflow: hidden;
  /*background: #1f1f1f url("@/assets/backgrounds/1.jpg") no-repeat center center fixed !important;*/
  background: #1f1f1f;
}
</style>
