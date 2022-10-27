<script setup>
import { ref } from 'vue';
import axios from 'axios'

let dataConnections = ref([])
let dataFilesSended = ref([])

const getAllConnections = () => {
  return axios
  .get('http://localhost:8000/connections')
  .then(response => (
    // console.log(response.data)
    dataConnections.value = response.data[0]
  ))
  .catch(error => console.log(error))
}

const getAllFilesSended = () => {
  return axios
  .get('http://localhost:8000/filesSended')
  .then(response => (
    // console.log(response.data)
    dataFilesSended.value = response.data[0]
  ))
  .catch(error => console.log(error))
}

</script>

<template>
  <div class="container text-center mt-3">
    <h1>File Server Information</h1>
    <button @click="getAllConnections">Info Channel conecctions</button>
    <div >
      <ul class="list-group">
        <li
          class="list-group-item"
          v-for="(channelConnections, index) in dataConnections" 
          :key="index"
        >
          {{ index }} - {{ channelConnections }}
        </li>
      </ul>
    </div>
    <button @click="getAllFilesSended" class="mt-4">Info files sended</button>
    <div >
      <ul class="list-group">
        <li
          class="list-group-item"
          v-for="(filesSended, index) in dataFilesSended" 
          :key="index"
        >
          {{ index }} - {{ filesSended }}
        </li>
      </ul>
    </div>
  </div>
</template>

<style>

</style>
