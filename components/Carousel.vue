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
        :autoplay="false"
        :speed="1000"
        :loop="true"
        :breakpoints="{
          320:{
            slidesPerView:1,
          },
          768:{
            slidesPerView: 2
          },
          1024:{
            slidesPerView: 4,
          }
        }"
    >
      <slot/>
    </swiper-container>
  </ClientOnly>
</template>

<style lang="css">
::part(pagination) {
  position: static;
  margin-top: 5px;
  --swiper-pagination-bullet-size: 11px;
}

@media only screen and (min-width: 1024px) {
  ::part(pagination) {
    margin-top: 20px;
  }
}
</style>
