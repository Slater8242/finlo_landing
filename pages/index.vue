<script setup lang="ts">
const slide = {
  id: 1,
  icon: "uil:clock",
  title: "Hipotekārais kredīts",
  description: "Aizdevums ar nekustamā īpašuma ķīlas nodrošinājumu. Īpašuma iegādei, esoša aizdevuma pārkreditācijai vai esoša īpašuma ieķīlāšana.",
  link: "#",
};
</script>

<template>
  <div class="content">
    <section class="hero">
      <div class="container">
        <div class="hero-content">
          <div class="hero-text">
            <h1>
              Mūsdienīga pieeja <br/>
              Aizdevumu izsniegšanai
            </h1>
            <p>
              Finlo darbības virziens ir aizdevumu izsniegšana ar nekustamā
              īpašuma nodrošinājumu jeb hipotekārais kredīts.
              <br/>
              Izprotot klientu vēlmes un vajadzības, esam izstrādājuši
              pieteikšanās un kredīta izvērtēšanas procedūru pēc iespējas ērtāku
              un klientam piemērotāku.
            </p>
            <Button label="Pieteikties" style="margin-top: 20px"/>
          </div>
          <div class="image">
<!--            <img src="/assets/images/background.png" alt="background" width="600" height="700">-->
          </div>
        </div>
      </div>
    </section>

    <section class="features">
      <div class="container">
        <h2>Our Features</h2>
        <div class="feature-grid">
          <div class="feature-card" v-for="n in 4">
            <Icon name="uil:clock" class="icon"/>
            <p>Request Appointment</p>
          </div>
        </div>
        <Button label="Pieteikties"/>
      </div>
    </section>

    <section class="text-photo">
      <div class="container" style="display: flex; max-width: 1200px">
        <div class="photo">
          <img src="/assets/images/03.jpg" alt="image" style="width: 500px">
        </div>
        <div class="text" style="text-align: left; margin-left: 60px">
          <div class="title">
            <h2 style="font-size: 50px;">
              Dedicated to Your
              <br>
              Health and Wellness
            </h2>
          </div>
          <p class="description" style="margin-top: 30px; margin-bottom: 30px; color: #6B6B6B;">
            At Mediweb, our mission is to provide exceptional healthcare services with a focus on patient-centered care.
            We are dedicated to improving the health and well-being of our community through.
          </p>
          <div class="qualities" style="display: flex; gap: 20px;">
            <div class="quality" v-for="n in 2" :key="n">
              <div class="single-quality" v-for="n in 3" :key="n" style="display: flex; align-items: center;">
                <Icon name="uil:check" style="font-size: 30px; color: #6A47ED"/>
                <span style="font-size: 18px">Comprehensive Care Services</span>
              </div>
            </div>
          </div>
          <Button label="Pieteikties" style="margin-top: 20px"/>
        </div>
      </div>
    </section>

    <section class="loan-types">
      <div class="container">
        <Carousel>
          <swiper-slide v-for="n in 10" :key="n">
            <div class="carousel-slide">
              <Icon :name="slide.icon" style="width: 60px; height: 60px"/>
              <p><strong>{{ slide.title }}</strong></p>
              <span>{{ slide.description }}</span>
              <a href="#">Learn more</a>
            </div>
          </swiper-slide>
        </Carousel>
      </div>
    </section>

    <section class="contact">
      <div class="container">
        <h2>Sazinies ar mums</h2>
        <a href="tel:+37167199909">67 19 99 09</a>
      </div>
    </section>
  </div>
  <FloatingWhatsapp/>
</template>

<style scoped>
a {
  text-decoration: none;
}

.contact {
  text-align: center;
  color: #fff;
  font-size: 30px;
  background-color: #625efd;
  background-image: url("/assets/images/cells.png");
  background-repeat: no-repeat;
  background-size: cover;
  background-blend-mode: overlay;
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

.hero {
  position: relative;
  padding: 35px 15px;
  /*background: #6A47ED;*/
  background-image: url("@/assets/images/background.png");
  background-size: cover;
  color: #615d5d;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  height: 600px;
}

.hero-content {
  display: flex;
  row-gap: 15px;
  align-items: center;
  flex-direction: column;
}

.features,
.contact,
.loan-types,
.text-photo{
  position: relative;
  margin-top: 30px;
  padding: 15px 15px;
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
  background-position: center;
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

@media only screen and (min-width: 768px) {
  .feature-grid {
    grid-template-columns: auto auto;
  }
}

@media only screen and (min-width: 1024px) {
  .hero .container {
    max-width: 1300px;
  }

  .hero-content {
    flex-direction: row;
  }

  .hero-text {
    h1 {
      font-size: 50px;
    }

    p {
      font-size: 25px;
    }
  }

  .features,
  .contact,
  .loan-types,
  .text-photo{
    margin-top: 100px;
  }

  .features::before {
    height: 85%;
  }

  .feature-grid {
    display: flex;
  }

  .feature-card {
    display: flex;
    align-items: center;

    p{
      font-size: 24px;
    }
  }

  .icon {
    width: 60px;
    height: 60px;
  }

  .contact{
    height: 400px;
    display: flex;
    align-items: center;
  }

  .contact h2{
    font-size: 86px;
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
    width: 280px;
    cursor: grab;
    a {
      border: 1px solid #625efd;
      border-radius: 20px;
      padding: 8px 20px;
      width: 140px;
    }

    span {
      font-size: 15px;
    }
  }
}
</style>
