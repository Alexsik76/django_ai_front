<template>
  <v-layout>
    <v-navigation-drawer v-model="drawer">
      <v-list density="comfortable" class="text-h5 mt-10" item-props :items="items" nav />
      <template #append>
        <v-list-item
          class="ma-2"
          link
          nav
          prepend-icon="mdi-cog-outline"
          title="Settings"
        />
      </template>
    </v-navigation-drawer>
    <v-app-bar class="ps-4" flat>
      <v-app-bar-nav-icon v-if="$vuetify.display.smAndDown" @click="drawer = !drawer" />
      <v-app-bar-title class="text-h6 text-md-h5 text-lg-h4">Демонстраційний WEB застосунок</v-app-bar-title>
      <template #append>
        <v-btn class="text-none me-2" height="48" icon slim>
          <v-avatar color="surface-light" image="https://cdn.vuetifyjs.com/images/john.png" size="32" />
          <v-menu activator="parent">
            <v-list density="compact" nav>
              <v-list-item append-icon="mdi-cog-outline" link title="Settings" />
              <v-list-item append-icon="mdi-logout" link title="Logout" />
            </v-list>
          </v-menu>
        </v-btn>
      </template>
    </v-app-bar>
    <router-view />
  </v-layout>
</template>
<script setup>
  import { ref } from 'vue'

  const drawer = ref(true)

  const items = ref([
    {
      title: 'Головна сторінка',
      prependIcon: 'mdi-view-dashboard-outline',
      link: true,
      href: '/'
    },
    {
      title: 'Викладачі',
      prependIcon: 'mdi-account-group',
      link: true,
      href: '/teachers'
    },
    {
      title: 'Предмети',
      prependIcon: 'mdi-briefcase-outline',
      link: true,
      href: '/disciplines'
    },
    {
      title: 'Завдання',
      prependIcon: 'mdi-calendar',
      link: true,
      href: '/tasks'
    },
    {
      title: 'Reports',
      prependIcon: 'mdi-file-chart-outline',
      link: true,
    },
  ])
</script>
<style>
.v-navigation-drawer--left{
  .v-list-item-title{
    font-size: large !important;
  }

}
</style>

