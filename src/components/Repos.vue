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
    <carousel>
      <slide v-for="(repo,i) in repos" :key="i" :class="['repos--repo', !repo.transform ? '' : 'rotate']" @click="transformCard(repo)">
        <div v-if="!repo.transform" class="front-card">
          <p v-text="repo.name"></p>
        </div>
        <div v-else class="back-card">
          <ul>
            <li>
              {{ repo.stargazers_count }}
              Estrelas
            </li>
            <li class="access">
              <a :href="repo.html_url" target="_blank" v-text="'Acessar'"></a>
            </li>
          </ul>
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
            .front-card{
              p{
                text-align: center;
                text-transform: capitalize;
              }
            }
            .back-card{
              ul{
                padding: 0;
                list-style-type: none;
                .access{
                  margin-top: 1rem;
                  a{
                    color: $green;
                    text-decoration: none;
                  }
                }
              }
            }
          }
          .rotate{
            animation: rotatecard;
            animation-duration: 1s;
            background: linear-gradient(to bottom, $dark, $dark2);
            border: 1px solid $green;
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
