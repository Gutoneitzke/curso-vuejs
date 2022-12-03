<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Navigation } from 'vue3-carousel'

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

const transformCard = (data: any) => {
  data.transform = !data.transform ? false : true
  data.transform = !data.transform
}

getReposFromGithub()

</script>

<template>
  <div v-if="repos" class="repos">
    <carousel :items-to-show="5">
      <slide v-for="(repo,i) in repos" :key="i" :class="['repos--repo', !repo.transform ? '' : 'rotate']" @mouseout="!repo.transform ? '' : transformCard(repo)" @click="transformCard(repo)">
        <div v-if="!repo.transform">
          <p v-text="repo.name"></p>
        </div>
        <div v-else>
          <p v-text="repo.stargazers_count"></p>
        </div>
      </slide>

      <template #addons>
        <navigation />
      </template>
    </carousel>
  </div>
  <p v-else>Nenhum registro</p>
</template>

<style lang="scss">
  .repos{
    .carousel{
      .carousel__viewport{
        .carousel__track{
          display: flex;
          align-items: center;
          gap: 1rem !important;
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
              text-transform: capitalize;
            }
          }
          .rotate{
            animation: rotatecard;
            animation-duration: 1s;
            background: linear-gradient(to bottom, $dark, $dark2);
          }
        }
      }
    }
  }
  @keyframes rotatecard {
    from {transform: rotateY(0deg);}
    to {transform: rotateY(360deg);}
  }
</style>
