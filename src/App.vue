<script setup lang="ts">
import { ref } from 'vue'
import Header from './components/Header.vue'
import SocialNetwork from './components/SocialNetwork.vue'
import Repos from './components/Repos.vue'

const languages = ref<Object>([
  'HTML',
  'CSS',
  'JavaScript',
  'Typescript',
  'Vue.js',
  'React.js',
  'Node.js',
  'PHP',
  'Laravel',
  'Mysql',
  'Mariadb'
])

</script>

<template>
  <div class="content">
    <header>
      <Header/>
    </header>
    <main>
      <div class="my-description">
        <img src="desenho.png" alt="">
        <div class="informations">
          <h2>Gustavo Neitzke</h2>
          <div class="informations--data">
            <p>Sit sit deserunt pariatur dolor do deserunt cupidatat labore minim Lorem consequat sunt. Minim magna quis amet et ut magna ad pariatur do nostrud id. Mollit do ipsum laboris elit officia amet sunt.</p>
            <p>Sit sit deserunt pariatur dolor do deserunt cupidatat labore minim Lorem consequat sunt. Minim magna quis amet et ut magna ad pariatur do nostrud id. Mollit do ipsum laboris elit officia amet sunt.</p>
          </div>
          <div class="informations--languages">
            <span v-for="(l,i) in languages" :key="i" v-text="l"></span>
          </div>
        </div>
      </div>
      <SocialNetwork />
    </main>
    <footer>
      <Repos />
    </footer>
  </div>
</template>

<style lang="scss" scoped>
  .content{
    main{
      display: flex;
      align-items: center;
      justify-content: center;
      flex-wrap: wrap;
      gap: 2rem;
      margin: 2rem;
      .my-description{
        display: flex;
        align-items: center;
        gap: 1rem;
        width: 58rem;
        .informations{
          display: flex;
          flex-direction: column;
          gap: 2rem;
          h2{
            font-size: 3rem;
            margin: 0;
          }
          .informations--languages{
            display: flex;
            justify-content: flex-start;
            flex-wrap: wrap;
            gap: 1rem;
            span{
              background-color: $grey;
              padding: .1rem 1rem;
              font-size: .8rem;
              border-radius: 1rem;
              transition: .4s;
              cursor: default;
            }
            span:hover{
              background-color: $green;
            }
          }
        }
      }
    }
    footer{
      margin: 2rem;
      h4{
        font-weight: 100;
      }
    }
  }

  @media (max-width: 768px)
  {
    main{
      margin: .4rem;
      img{
        display: none;
      }
    }
  }
</style>
