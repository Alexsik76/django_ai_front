<template>
  <v-main>
    <div class="pa-4">
      <div class="d-flex justify-center ma-2 pa-2 text-h5">
        Список предметів
      </div>
      <v-banner v-if="error" class="my-4" color="warning" icon="$warning" lines="three">
        <v-banner-text>
          Data empty or not loaded from backend <br>
          {{ error }}
        </v-banner-text>
      </v-banner>
      <v-table v-else theme="dark">
        <thead>
          <tr class="text-h6 text-center">
            <th class="text-center">
              Предмет
            </th>
            <th class="text-center">
              Викладач
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-if="isFetching">
            <v-skeleton-loader type="list-item-two-line"></v-skeleton-loader>
          </tr>
          <tr v-else-if="data" v-for="item in data" :key="item.last_name">
            <td>{{ item.name }}</td>
            <td>{{ item.teacher}}</td>
          </tr>
        </tbody>
      </v-table>
    </div>
  </v-main>
</template>
<script setup>
import { useFetch } from '@vueuse/core'
const base_url = import.meta.env.VITE_API_URL
const url = `${base_url}disciplines/`
const { isFetching, error, data } = useFetch(url).get().json()
</script>