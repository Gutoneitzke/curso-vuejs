<template>
  <div class="header">
    <div class="box-image">
      <img src="gn.png" alt="Foto de perfil">
    </div>
    <h1>Olá! Seja bem-vindo ao perfil de <strong>Gustavo Neitzke</strong></h1>
  </div>
</template>

<style lang="scss" scoped>
  .header{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    padding: 2rem;
    border-bottom: 1px solid $gray;
    .box-image{
      height: 70px;
      width: 70px;
      background-color: $green;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      img{
        width: 100%;
        border-radius: 50%;
      }
    }
    h1{
      color: $white;
      margin: 0;
      font-weight: 100;
      strong{
        color: $green;
      }
    }
  }
</style>
