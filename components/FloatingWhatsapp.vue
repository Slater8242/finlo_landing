<script setup lang="ts">

</script>

<template>
  <NuxtLink to="https://wa.me/+37122726944" target="_blank" rel="noopener noreferrer">
    <Icon name="uil:whatsapp"/>
  </NuxtLink>
</template>

<style scoped>
a{
  position: fixed;
  bottom: 20px;
  right: 20px;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  padding: 5px;
  background-color: #25D366;
  z-index: 5;
}

:where(.i-uil\:whatsapp){
  color: #fff;
  font-size: 30px;
}

@media only screen and (min-width: 1024px) {
  a{
    width: 60px;
    height: 60px;
    padding: 7px;
  }

  :where(.i-uil\:whatsapp){
    font-size: 46px;
  }
}

</style>