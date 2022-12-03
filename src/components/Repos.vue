<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'

let repos = ref<Object>([])

const getReposFromGithub = () => {
  axios
    .get('https://api.github.com/users/Gutoneitzke/repos')
    .then((response: any) => {
      repos.value = response.data
      console.log(repos.value)
    })
    .catch((e: any) => {
      console.log(e)
    })
}

getReposFromGithub()

</script>

<template>
  <div v-if="repos" class="repos">
    <div v-for="(repo,i) in repos" :key="i" class="repos--repo">
      <p v-text="repo.name"></p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  
</style>
