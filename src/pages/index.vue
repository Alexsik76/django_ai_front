<template>
  <v-main>
    <div class="pa-4">
      <p>Main</p>
      <p>API URL: {{ baseurl }}</p>
    </div>
  </v-main>
</template>
<script setup>
const baseurl = import.meta.env.VITE_API_URL
</script>
