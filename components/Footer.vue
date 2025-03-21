<script setup lang="ts">
import Logo from "@/assets/icons/logo.svg"

const services = [
  {title: "Hipotekārais kredīts", icon:"uil:home-alt"},
  {title: "Biznesa attīstībai", icon:"uil:suitcase"},
  {title: "Ēku būvniecībai", icon:"uil:constructor"},
  {title: "Kredītu apvienošana", icon:"fa6-solid:arrows-to-circle"},
  {title: "Zemniekiem", icon:"iconoir:farm"},
  {title: "Auto līzings", icon:"uil:car-sideview"},
]
</script>

<template>
  <footer>
    <div class="container">
      <Logo style="width: 150px; height: 150px; opacity: 0.5" />
      <div class="socials">
        <span>Sociālie tīkli</span>
        <div class="links">
          <NuxtLink>
            <Icon name="uil:twitter" size="large" />
          </NuxtLink>
          <NuxtLink>
            <Icon name="uil:facebook" size="large" />
          </NuxtLink>
          <NuxtLink>
            <Icon name="uil:linkedin" size="large" />
          </NuxtLink>
        </div>
      </div>
      <div class="nav-bar">
        <div class="services">
          <span>Pakalpojumi</span>
          <ul class="list-style service-list">
            <li v-for="service in services" :key="service.title" class="service-item">
              <NuxtLink :to="service.title">{{service.title}}</NuxtLink>
            </li>
          </ul>
        </div>
        <div class="other">
          <span>Cits</span>
          <ul class="list-style">
            <li>
              <NuxtLink to="#">Par mums</NuxtLink>
            </li>
            <li>
              <NuxtLink to="#">Kontakti</NuxtLink>
            </li>
            <li>
              <NuxtLink to="#">BUJ</NuxtLink>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
footer {
  background-color: #3A405A;
  color: white;
  padding: 40px 0;
}

.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.links{
  display: flex;
  justify-content: center;
  column-gap: 10px;
  margin-top: 15px;
}

.links span{
  cursor: pointer;
}

:where(.i-uil\:twitter):hover{
  color: #1DA1F2;
  opacity: 1 !important;
}
:where(.i-uil\:facebook):hover{
  color: #1877F2;
  opacity: 1 !important;
}
:where(.i-uil\:linkedin):hover{
  color: #0A66C2;
  opacity: 1 !important;
}

.nav-bar{
  display: flex;
  column-gap: 20px;
}

.list-style {
  padding: 0;
  list-style: none;
}

.nav-bar span, .socials span{
  opacity: 0.5;
}

.nav-bar a{
  text-decoration: none;
  color: white;
  font-weight: 200;
  letter-spacing: 0.3px;
}

 .nav-bar a:hover{
  opacity: 0.5;
}
</style>