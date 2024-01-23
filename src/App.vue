<script setup>

  import axios from "axios";
  import {reactive, ref} from "vue";



  let data = ref()
  const url = 'https://api.nasa.gov/planetary/apod?api_key=1dcwKQzU4RaaUJOP5j0Hleub5KCO4HMDl6tkk3Fw'

  let nasaImage = ref('')
  let nasaDate = ref('')
  let nasaCopy = ref('')
  let nasaTitle = ref('')

  axios.get(url)
        .then(response => {
          data.value = response.data
          nasaImage.value = response.data.hdurl
          nasaDate.value = response.data.date
          nasaCopy.value = response.data.explanation
          nasaTitle.value = response.data.title
        })

  console.log(data)


</script>

<template>

  <div class="image-wrapper">
    <h1>{{nasaTitle}}</h1>
    <h1>{{nasaDate}}</h1>
    <h1>{{nasaCopy}}</h1>
    <img v-bind:src = 'nasaImage' alt = ''>

  </div>

</template>

<style scoped>
header {
  line-height: 1.5;
}

</style>
