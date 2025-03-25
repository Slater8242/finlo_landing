<script setup lang="ts">
const slide = {
  id: 1,
  icon: "uil:clock",
  title: "Hipotekārais kredīts",
  description: "Aizdevums ar nekustamā īpašuma ķīlas nodrošinājumu. Īpašuma iegādei, esoša aizdevuma pārkreditācijai vai esoša īpašuma ieķīlāšana.",
  link: "#",
};

const carouselConfig = {
  // autoplay: 5000,
  height: 400,
  itemsToShow: 3,
  gap: 20,
  wrapAround: true,
};
</script>

<template>
  <div class="content">
    <section class="hero">
      <div class="container">
        <div class="hero-content">
          <div class="hero-text">
            <h1>
              Mūsdienīga pieeja <br />
              Aizdevumu izsniegšanai
            </h1>
            <p>
              Finlo darbības virziens ir aizdevumu izsniegšana ar nekustamā
              īpašuma nodrošinājumu jeb hipotekārais kredīts.
              <br />
              Izprotot klientu vēlmes un vajadzības, esam izstrādājuši
              pieteikšanās un kredīta izvērtēšanas procedūru pēc iespējas ērtāku
              un klientam piemērotāku.
            </p>
            <Button label="Pieteikties" />
          </div>
          <div class="image">
            <img src="/assets/images/hero-image.png" alt="">
          </div>
        </div>
      </div>
    </section>

    <section class="features">
      <div class="container">
        <h2>Our Features</h2>
        <div class="feature-grid">
          <div class="feature-card" v-for="n in 4">
            <Icon name="uil:clock" class="icon" />
            <p>Request Appointment</p>
          </div>
        </div>
        <Button label="Pieteikties" styling="style-2"/>
      </div>
    </section>

    <section class="loan-types">
      <div class="container">
        <Carousel v-bind="carouselConfig">
          <Slide v-for="n in 5" :key="slide.id">
            <div class="carousel-slide">
              <Icon :name="slide.icon" style="width: 60px; height: 60px"/>
              <p><strong>{{ slide.title }}</strong></p>
              <span>{{ slide.description }}</span>
              <a href="#">Learn more</a>
            </div>
          </Slide>
          <template #addons>
            <Pagination />
          </template>
        </Carousel>
      </div>
    </section>

    <section class="about">
      <div class="container">
        <h2>Why Choose Us?</h2>
        <p>
          We provide seamless financial services with top-tier security and
          convenience.
        </p>
      </div>
    </section>

    <section class="contact">
      <div class="container">
        <h2>Sazinies ar mums</h2>
        <a href="tel:+37167199909">67 19 99 09</a>
      </div>
    </section>
  </div>
</template>

<style scoped>
a{
  text-decoration: none;
}

.contact {
  text-align: center;
  color: #fff;
  font-size: 30px;
  background-color: #625efd;
  a {
    background-color: #fff;
    padding: 10px 15px;
    margin: 10px 0;
    border-radius: 20px;
    color: #625efd;
    display: inline-block;
  }
}

.content {
  text-align: center;
}

.cta-button {
  padding: 12px 24px;
  border: none;
  background: #007bff;
  color: white;
  font-size: 18px;
  font-weight: bold;
  cursor: pointer;
  border-radius: 10px;
  transition: 0.3s;
}

.hero {
  position: relative;
  padding: 35px 15px;
  background: #6A47ED;
  color: white;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  z-index: 0;
  height: 710px;
}

.hero-content {
  display: flex;
  row-gap: 15px;
  align-items: center;
  flex-direction: column;
}

.about,
.features,
.contact, .loan-types {
  position: relative;
  margin-top: 30px;
  padding: 15px 15px;
}

.hero::before {
  display: block;
  content: "";
  top: 0;
  right: 0;
  position: absolute;
  width: 472px;
  height: 100%;
  /* background-image: url("@/assets/images/fintech-abstract.jpg"); */
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
  z-index: -1;
}

.features::before {
  display: block;
  content: "";
  top: 0;
  right: 0;
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: url("@/assets/icons/logo.svg");
  background-repeat: no-repeat;
  background-size: contain;
  background-position: top right;
  z-index: -1;
  opacity: 0.04;
}

.feature-grid {
  display: grid;
  justify-items: center;
  grid-template-columns: auto;
  justify-content: center;
  gap: 20px;
  margin-top: 30px;
  margin-bottom: 30px;
}

.feature-card {
  /* width: 240px; */
  background: rgba(255, 255, 255, 0.3);
  padding: 35px 20px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  text-align: center;
}

.contact-card {
  background-color: rgba(38, 31, 179, 0.5);
}

@media only screen and (min-width: 768px) {
  .feature-grid {
    grid-template-columns: auto auto;
  }
}

@media only screen and (min-width: 1024px) {
  .hero .container{
    max-width: 1300px;
  }

  .hero-content{
    flex-direction: row;
  }

  .hero-text{
    h1{
      font-size: 50px;
    }

    p{
      font-size: 25px;
    }
  }

  .features::before {
    width: 55%;
    height: 115%;
  }

  .feature-grid {
    display: flex;
  }

  .feature-card {
    display: flex;
  }

  .icon {
    width: 60px;
    height: 60px;
  }

  .carousel-slide {
    border: 1px solid #625efd;
    border-radius: 10px;
    padding: 15px 25px;
    display: flex;
    flex-direction: column;
    text-align: left;
    gap: 20px;
    height: 350px;
    
    a{
      border: 1px solid #625efd;
      border-radius: 20px;
      padding: 8px 20px;
      width: 140px;
    }

    span{
      font-size: 15px;
    }
  }
}
</style>
