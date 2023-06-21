<template>
  <v-app>
    <v-app-bar title="Saunter" color="blue-lighten-5">
      <v-btn variant="elevated" text="Add path" color="blue-lighten-1" />
    </v-app-bar>
    <SideBar />
    <v-main class="d-flex align-center justify-center" style="min-height: 300px;">
      Main Content
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
  import SideBar from './components/SideBar.vue';
</script>
