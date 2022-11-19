<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ msg: string }>()

const count = ref(0)
</script>

<template>
  <div class="content">
    <div class="box-image"></div>
    <h1>Olá! Meu nome é <strong>Gustavo Neitzke</strong></h1>
  </div>
</template>

<style lang="scss" scoped>
  .content{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    padding: 2rem;
    .box-image{
      height: 70px;
      width: 70px;
      background-color: $green;
      border-radius: 50%;
    }
    h1{
      color: $white;
      margin: 0;
      strong{
        color: $green;
      }
    }
  }
</style>
