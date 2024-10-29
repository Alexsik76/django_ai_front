<template>
  <v-main>
    <div class="pa-4">
      <div class="d-flex justify-center mb-6">
        <v-sheet class="ma-2 pa-2 text-h4">
          Список викладачів
        </v-sheet>
      </div>
        <v-banner v-if="error" class="my-4" color="warning" icon="$warning" lines="three">
          <v-banner-text>
            Data empty or not loaded from backend <br>
            {{ error }}
          </v-banner-text>
        </v-banner>
        <v-table v-else theme="dark">
          <thead>
            <tr>
              <th class="text-left">
                Прізвище, ім'я, по батькові
              </th>
              <th class="text-left">
                Предмет
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-if="isFetching">
              <v-skeleton-loader type="list-item-two-line"></v-skeleton-loader>
            </tr>
            <tr v-else-if="data" v-for="item in data.teachers" :key="item.name">
              <td>{{ item.name }}</td>
              <td>{{ item.calories }}</td>
            </tr>
          </tbody>
        </v-table>
    </div>
  </v-main>
</template>
<script setup>
import { useFetch } from '@vueuse/core'
const url = "http://localhost:8000/api/schedule/teachers"
const { isFetching, error, data } = useFetch(url)
</script>