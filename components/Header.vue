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

const links = [
  {name: "twitter", icon:"uil:twitter"},
  {name: "facebook", icon:"uil:facebook"},
  {name: "linkedin", icon:"uil:linkedin"},
]
</script>

<template>
  <header class="header">
    <div class="header-contact">
      <div class="container">
        <div class="left">
          <div class="address">
            <Icon name="uil:map-marker"/>
            <span>Bukultu iela 11, Rīga, LV-1005</span>
          </div>
          <div class="working-hours">
            <Icon name="uil:clock"/>
            <span>Pirmdiena-Piektdiena: 08-17</span>
          </div>
        </div>
        <div class="right">
          <div class="contact">
            <Icon name="uil:phone"/>
            <span>67 19 96 06</span>
          </div>
          <div class="socials">
            <span>Sociālie tīkli</span>
            <NuxtLink to="#" v-for="link in links" :key="link.name">
              <Icon :name="link.icon" style="color: white"/>
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
    <div class="navbar container">
      <a href="#">
        <SvgoLogo class="logo"/>
      </a>
      <Icon class="menu-button" name="ic:round-menu" style="width: 35px; height: 35px;" @click="menu = !menu"/>
      <nav :class="[menu ? 'menu-open' : 'menu-closed', 'nav']">
        <Icon name="ri:close-large-line"  class="close-button" @click="menu=!menu"/>
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
      <div class="login-lang">
        <Button label="Login"/>
        <Button label="LV"/>
      </div>
    </div>
  </header>
</template>

<style scoped>
.header{
  position: sticky;
  top: 0;
  padding-bottom: 20px;
  z-index: 5;
  background-color: #6A47ED;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  color: #fff;
}

.header-contact{
  padding: 10px 0;
  background-color: #3f2a87;
}

.header-contact .container{
  display: flex;
  justify-content: space-between;
}

.left, .right {
  display: flex;
  gap: 40px;
}

.address, .working-hours, .contact{
  display: flex;
  align-items: center;
  gap: 5px;
}

.navbar{
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 20px;
}

.menu-closed{
  display: none;
}

.menu-open{
  position: absolute;
  top: 0;
  left: 0;
  background-color: #fff;
  height: 100vh;
  width: 100%;
}

.nav ul{
  list-style-type: none;
}

.nav-list{
  display: flex;
  flex-direction: column;
  align-items: center;
  list-style-type: none;
  gap: 20px;
  margin-top: 80px;
  text-align: center;
}

.close-button{
  position: absolute;
  top: 30px;
  left: 30px;
}

.logo{
  width: 120px;
  height: 30px;
  color: #fff;
  cursor: pointer;
}

a{
  text-decoration: none;
}

.nav-item {
  color: inherit;
  transition: 0.3s;
}

.service-item{
  display: flex;
  align-items: center;
  gap: 15px;
  padding: 5px 10px;
  border-radius: 10px;
  color: #000;
  transition: 0.3s;
}

.service-item:hover{
  background-color: rgba(0, 0, 0, .1);
}

.nav-item:hover {
  color: #000;
}

@media only screen and (min-width: 1024px){
  .nav{
    position: static;
    width: auto;
    height: auto;
    background: transparent;
    box-shadow: none;
    display: flex;
    align-items: center;
  }

  .nav-list{
    flex-direction: row;
    margin: 0;
  }

  .menu-button, .close-button{
    display: none;
  }

  .logo{
    width: 164px;
    height: 45px;
  }

  .services{
    position: relative;
    span{
      cursor: pointer;
    }
  }

  .service-list{
    position: absolute;
    margin-top: 10px;
    padding: 20px;
    background-color: white;
    font-size: 15px;
    display: grid;
    grid-template-columns: auto auto auto;
    gap: 15px 10px;
    box-shadow: 0 3px 10px rgba(0, 0, 0, .3);
    border-radius: 10px;
  }

  .login-lang{
    display: flex;
    gap: 15px;
    align-items: center;
  }
}
</style>