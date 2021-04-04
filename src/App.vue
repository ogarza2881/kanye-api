<template>
<div class=" py-8  ">
<img class="w-100 verticle-align: middle" src="./assets/kanye.jpg" alt="Kanye" /><br><br>
  <button @click="getKanye">Click Here to Get Kanye's Quote of the Day</button><br><br>
  <ul>
    <li>Kanye says, "{{kanye.quote}}."</li>
  </ul><br><br>
  <button @click="getKanye">Click Here for Another Quote!</button>
  </div>
</template>

<script setup>
import {ref} from 'vue'
import axios from 'axios'

const kanye = ref([])

const quotesAPI = axios.create({
  baseURL: 'https://api.kanye.rest',
})

const getKanye = async () => {
  const resource = 'kanye'
  const response = await quotesAPI(resource)
  kanye.value = response.data
}
</script>
