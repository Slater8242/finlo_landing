<script setup lang="ts">
const show = ref(false);
const menu = ref(false);

const toggleShow = ()=>{
  show.value = !show.value
}

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
  <header class="header">
    <div class="navbar container">
      <a href="#" class="logo">
        <SvgoLogo style="width: 164px; height: 45px; color: #261FB3;"/>
      </a>
      <nav class="nav" v-if="menu">
        <ul class="nav-list">
          <li><a href="#about" class="nav-item">Sākums</a></li>
          <li class="services nav-item" @click="toggleShow">
            <span>Pakalpojumi</span>
            <Icon v-if="!show" name="ic:baseline-keyboard-arrow-down"/>
            <Icon v-if="show" name="ic:baseline-keyboard-arrow-up"/>
            <ul v-if="show" class="service-list">
              <li v-for="service in services" :key="service.title">
                <NuxtLink :to="service.title" class="service-item">
                  <Icon :name="service.icon" style="width: 25px; height: 25px;"/>
                  {{ service.title }}
                </NuxtLink>
              </li>
            </ul>
          </li>
          <li><NuxtLink to="#features" class="nav-item">Kā pieteikties?</NuxtLink></li>
          <li><NuxtLink to="#why-us" class="nav-item">Kāpēc mēs?</NuxtLink></li>
          <li><NuxtLink to="#faq" class="nav-item">BUJ</NuxtLink></li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.header{
  position: sticky;
  top: 0;
  padding: 20px 0;
  z-index: 5;
  background-color: rgba(255, 255, 255, 0.85);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}


@media only screen and (min-width: 1280px){
  .header{
    position: sticky;
    top: 0;
    padding: 20px 0;
    z-index: 5;
    background-color: rgba(255, 255, 255, 0.85);
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  }

  .navbar{
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo{
    cursor: pointer;
  }

  .nav-list{
    list-style: none;
    display: flex;
    gap: 20px;
  }

  .nav a {
    text-decoration: none;
    color: #333;
    /* font-weight: bold; */
    transition: 0.3s;
  }

  .nav-item:hover {
    color: var(--primary-color);
  }

  .services{
    position: relative;
    span{
      cursor: pointer;
    }
  }

  .service-list{
    position: absolute;
    width: 470px;
    margin-top: 10px;
    padding: 20px;
    background-color: white;
    font-size: 15px;
    display: grid;
    grid-template-columns: auto auto auto;
    gap: 15px 10px;
    /* border: 1px solid black; */
    box-shadow: 0 3px 10px rgba(0, 0, 0, .3);
    border-radius: 10px;
    list-style: none;
  }

  .service-item{
    display: flex;
    align-items: center;
    column-gap: 15px;
    padding: 5px 10px;
    border-radius: 10px;
  }

  .service-item:hover{
    background-color: rgba(0, 0, 0, .1);
  }
}
</style>