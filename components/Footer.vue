<script setup lang="ts">
const services = [
  {title: "Hipotekārais kredīts", icon:"uil:home-alt", link:"mortgage-loan"},
  {title: "Biznesa attīstībai", icon:"uil:suitcase", link:"business-loan"},
  {title: "Ēku būvniecībai", icon:"uil:constructor", link:"construction-loan"},
  {title: "Kredītu apvienošana", icon:"fa6-solid:arrows-to-circle", link:"loan-consolidation"},
  {title: "Zemniekiem", icon:"iconoir:farm", link:"farm-loan"},
]
</script>

<template>
  <footer>
    <div class="container">
      <SvgoLogo class="logo"/>
      <div class="socials">
        <span>Sociālie tīkli</span>
        <div class="links">
          <NuxtLink>
            <Icon name="uil:facebook" class="social-icon"/>
          </NuxtLink>
          <NuxtLink>
            <Icon name="uil:linkedin" class="social-icon"/>
          </NuxtLink>
        </div>
      </div>
      <div class="nav-bar">
        <div class="services">
          <span>Pakalpojumi</span>
          <ul class="list-style service-list">
            <li v-for="service in services" :key="service.title" class="service-item">
              <NuxtLink :to="`/services/${service.link}`">{{service.title}}</NuxtLink>
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
            <li>
              <NuxtLink to="/privacy-policy">Privātuma politika</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/terms-of-use">Lietošanas noteikumi</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/DI_MGMT_Licence_ar_jauno_SIA_nosaukumu.pdf" target="_blank" external>Licence Nr.2016-026</NuxtLink>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
footer {
  background-color: #3f2a87;
  color: white;
  padding: 20px 0;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  gap: 30px;
}

.logo{
  width: 120px;
  height: 40px;
  opacity: 0.5
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

.social-icon{
  width: 25px;
  height: 25px;
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
  text-align: center;
  flex-direction: column;
  gap: 20px;
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

@media only screen and (min-width: 1024px){
  footer{
    padding: 40px 0;
  }

  .container, .nav-bar{
    flex-direction: row;
  }

  .socials span{
    font-size: 25px;
  }

  .nav-bar{
    text-align: left;
    gap: 30px;
  }

  .logo{
    width: 150px;
    height: 50px;
  }
}
</style>