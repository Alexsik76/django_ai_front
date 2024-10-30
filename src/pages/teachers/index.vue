<template>
  <v-main>
    <div class="pa-4">
      <div class="d-flex justify-center ma-2 pa-2 text-h5">
        Список викладачів
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
              Прізвище, ім'я, по батькові
            </th>
            <th class="text-center">
              Предмет
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-if="isFetching">
            <v-skeleton-loader type="list-item-two-line"></v-skeleton-loader>
          </tr>
          <tr v-else-if="data" v-for="item in data" :key="item.last_name">
            <td>{{ item.full_name }}</td>
            <td>{{ item.discipline.toString() }}</td>
          </tr>
        </tbody>
      </v-table>
    </div>
  </v-main>
</template>
<script setup>
import { useFetch } from '@vueuse/core'
const url = "https://ai.zpi-zp31.vn.ua/api/teachers/"
const { isFetching, error, data } = useFetch(url).get().json()
</script>