<script setup lang="ts">

</script>

<template>
  <ClientOnly>
    <swiper-container
        :pagination="{
          clickable: true,
        }"
        :slides-per-view="4"
        :space-between="20"
        :autoplay="true"
        :speed="1000"
        :loop="true"
    >
      <slot/>
    </swiper-container>
  </ClientOnly>
</template>

<style lang="css">
::part(pagination) {
  position: static;
  margin-top: 20px;
  --swiper-pagination-bullet-size: 11px;
}
</style>
