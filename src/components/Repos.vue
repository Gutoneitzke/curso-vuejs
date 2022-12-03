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
  <p v-else>Nenhum registro</p>
</template>

<style lang="scss" scoped>
  .repos{
    display: flex;
    align-items: center;
    gap: 1rem;
    .repos--repo{
      min-width: 140px;
      min-height: 140px;
      max-width: 140px;
      max-height: 140px;
      background: linear-gradient(to bottom, $green, $dark2);
      border-radius: 1rem;
      padding: 1rem;
      box-sizing: border-box;
      display: flex;
      justify-content: center;
      align-items: flex-end;
      p{
        text-align: center;
      }
    }
  }
</style>
