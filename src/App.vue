<script setup lang="ts">
import Header from './components/Header.vue'
</script>

<template>
  <div class="content">
    <header>
      <Header/>
    </header>
    <main>
      <div class="content--left">
        <img src="desenho.png" alt="">
        <div class="left--informations">
          <h2>Gustavo Neitzke</h2>
          <p>Sit sit deserunt pariatur dolor do deserunt cupidatat labore minim Lorem consequat sunt. Minim magna quis amet et ut magna ad pariatur do nostrud id. Mollit do ipsum laboris elit officia amet sunt.</p>
        </div>
      </div>
      <div class="content--right">
        componente das redes sociais
      </div>
    </main>
  </div>
</template>

<style lang="scss" scoped>
  .content{
    main{
      display: grid;
      grid-template-columns: 3fr 1fr;
      align-items: center;
      gap: 1rem;
      margin: 2rem;
      min-height: 50vh;
      .content--left{
        display: flex;
        align-items: center;
        gap: 1rem;
        h2{
          font-size: 3rem;
        }
      }
      .content--right{

      }
    }
  }
</style>
