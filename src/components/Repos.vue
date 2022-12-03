<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'

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
  <h5>Meus repositório no Github</h5>
  <div v-if="repos" class="repos">
    <div v-for="(repo,i) in repos" :key="i" :class="['repos--repo', !repo.transform ? '' : 'rotate']" @click="transformCard(repo)">
      <div v-if="!repo.transform" class="front-card">
        <p v-text="repo.name"></p>
      </div>
      <div v-else class="back-card">
        <ul>
          <li class="box-stars">
            <span v-text="repo.stargazers_count"></span>
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-star-fill" viewBox="0 0 16 16">
              <path d="M3.612 15.443c-.386.198-.824-.149-.746-.592l.83-4.73L.173 6.765c-.329-.314-.158-.888.283-.95l4.898-.696L7.538.792c.197-.39.73-.39.927 0l2.184 4.327 4.898.696c.441.062.612.636.282.95l-3.522 3.356.83 4.73c.078.443-.36.79-.746.592L8 13.187l-4.389 2.256z"/>
            </svg>
          </li>
          <li class="box-access">
            <a :href="repo.html_url" target="_blank" v-text="'Acessar'"></a>
          </li>
        </ul>
      </div>
    </div>
  </div>
  <p v-else>Nenhum registro</p>
</template>

<style lang="scss">
  .repos{
    display: flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
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
          .box-stars{
            display: flex;
            align-items: baseline;
            justify-content: center;
            gap: .4rem;
            font-size: 1.8rem;
            svg{
              color: $green;
            }
          }
          .box-access{
            margin-top: 1rem;
            a{
              color: $green;
              text-decoration: none;
              transition: .4s;
              &:hover{
                color: $green2;
              }
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
  @keyframes rotatecard {
    from {transform: rotateY(0deg);}
    to {transform: rotateY(360deg);}
  }
</style>
