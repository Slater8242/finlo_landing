<script setup lang="ts">
const slides = [
  {
    icon: "mdi:currency-usd-off",
    title: "Kredītu apvienošana",
    description:
      "Apvienojiet vairākus kredītus vienā, samazinot ikmēneša maksājumu un vienkāršojot finanšu plānošanu.",
    link: "#",
  },
  {
    icon: "mdi:hammer-wrench",
    title: "Īpašuma remontam",
    description:
      "Finansējums mājokļa vai komercobjekta remontam, lai palielinātu tā vērtību un uzlabotu dzīves kvalitāti.",
    link: "#",
  },
  {
    icon: "mdi:tractor",
    title: "Zemniekiem",
    description:
      "Finansējums lauksaimniecības tehnikas remontam un uzturēšanai, nodrošinot nepārtrauktu saimniecības darbību",
    link: "#",
  },
  {
    icon: "mdi:bank-transfer",
    title: "Pārkreditācija",
    description:
      "Labāki nosacījumi esošo kredītsaistību refinansēšanai, lai samazinātu procentu likmi un kopējās izmaksas.",
    link: "#",
  },
  {
    icon: "mdi:wallet",
    title: "Apgrozāmajiem līdzekļiem",
    description:
      "Aizdevums sezonālajām izmaksām, sēklām, degvielai un citiem saimniecības darbībai nepieciešamajiem resursiem.",
    link: "#",
  },
  {
    icon: "mdi:chart-line",
    title: "Biznesa attīstībai",
    description:
      "Kapitāls jaunu projektu realizēšanai, uzņēmuma izaugsmei un konkurētspējas uzlabošanai.",
    link: "#",
  },
];

const features = [
  { title: "Licencēts aizdevējs", icon: "mdi:certificate" },
  { title: "NĪ nodrošināti kredīti", icon: "mdi:home-lock" },
  { title: "Tirgū no 2008. gada", icon: "mdi:calendar-check" },
  { title: "Kreditējam visā LV", icon: "game-icons:latvia" },
];

const accordionItems = [
  {
    title: "Vai iespējams kredītu atdot ātrāk?",
    content: "Jā, kredītu pirms termiņa iespējams atdot ātrāk.",
  },
  {
    title: "Vai daļu kredīta iespējams saņemt uzreiz?",
    content:
      "Steidzamu biznesa jautājumu risināšanai, varam izvērtēt daļu finansējuma izsniegt līguma parakstīšanas dienā.",
  },
  {
    title: "Ja aizdevumu ņemu kredītu apvienošanai, kurš dzēsīs kredītus?",
    content:
      "FINLO aizdevumu pārskaitīs uz Jūsu norēķinu bankas kontu, līdz ar to Jūs būsiet atbildīgs par kredītu dzēšanu un maksājuma uzdevumu iesniegšanu dzēšanas apliecināšanai FINLO.",
  },
  {
    title: "Vai īpašumam tiks veikts nekustamā īpašuma novērtējums?",
    content: "Jā, mēs pasūtam sertificēta vērtētāja īpašuma novērtējumu.",
  },
  {
    title: "Kāda ir procentu likme?",
    content: "Procentu likme pie Finlo ir no 10% + 6 mēn. EURIBOR gadā",
  },
];

const qualities = [
  "Piedāvājums dienas laikā",
  "Pielāgots atmaksas grafiks",
  "Dinamiska apkapošana",
  "Individuāla pieeja",
  "Noslēdz attālināti",
  "Minimāla birokrātija",
];
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
            <Button label="Pieteikties" style="margin-top: 20px" />
          </div>
        </div>
      </div>
    </section>

    <section class="features">
      <div class="container">
        <h2>Our Features</h2>
        <div class="feature-grid">
          <div class="feature-card" v-for="feature in features">
            <Icon :name="feature.icon" class="icon" />
            <p>{{ feature.title }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="service">
      <div class="container">
        <img src="/assets/images/03.jpg" alt="image" class="service-image"/>
        <div class="service-text">
          <div class="service-title">
            <h2>Personiska pieeja un profesionāla apkalpošana</h2>
          </div>
          <p class="service-description" style="">
            Finlo darbības virziens ir aizdevumu izsniegšana ar nekustamā
            īpašuma nodrošinājumu jeb hipotekārais kredīts. Izprotot klientu
            vēlmes un vajadzības, esam izstrādājuši pieteikšanās un kredīta
            izvērtēšanas procedūru pēc iespējas ērtāku un klientam piemērotāku.
          </p>
          <div class="service-quality">
            <div
              class="single-quality"
              v-for="(quality, index) in qualities"
              :key="index"
            >
              <Icon name="uil:check" style="font-size: 30px; color: #6a47ed" />
              <span style="font-size: 18px">{{ quality }}</span>
            </div>
          </div>
          <Button label="Pieteikties" style="margin-top: 20px" />
        </div>
      </div>
    </section>

    <section class="loan-types">
      <div class="container">
        <h1 class="loan-types-title">
          Mūsu pakalpojumu klāsts
        </h1>
        <Carousel>
          <swiper-slide v-for="(slide, index) in slides" :key="index">
            <div class="carousel-slide">
              <Icon :name="slide.icon" class="icon" />
              <strong class="slide-title">{{ slide.title }}</strong>
              <span class="slide-description">{{ slide.description }}</span>
              <a href="#">Learn more</a>
            </div>
          </swiper-slide>
        </Carousel>
      </div>
    </section>

    <section class="faq">
      <div class="container">
        <h1 class="faq-title">Biežāk uzdotie jautājumi</h1>
        <Accordion :items="accordionItems" />
      </div>
    </section>

    <section class="contact">
      <div class="container">
        <h2>Sazinies ar mums</h2>
        <a href="tel:+37167199909">67 19 99 09</a>
      </div>
    </section>
  </div>
  <FloatingWhatsapp />
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
  background-color: #6a47ed;
  background-image: url("@/assets/images/transparnt_bg.png");
  background-size: cover;
  color: #fff;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
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
.service {
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
  gap: 20px;
  margin-top: 30px;
  margin-bottom: 30px;
}

.feature-card {
  width: 100%;
  background: rgba(255, 255, 255, 0.3);
  padding: 35px 20px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  text-align: center;
}

.service-image{
  width: 100%;
}

.loan-types {
  background-color: #f1f1ff;

  h1{
    font-size: 30px;
  }
}

.icon {
    width: 40px;
    height: 40px;
    color: #6a47ed;
  }

.carousel-slide{
  border: 1px solid #625efd;
  border-radius: 10px;
  padding: 15px 25px;
  display: flex;
  flex-direction: column;
  text-align: left;
  gap: 10px;
  cursor: grab;
}

.slide-description{
  font-size: 14px;
}

@media only screen and (min-width: 768px) {
  .feature-grid {
    grid-template-columns: auto auto;
  }
}

@media only screen and (min-width: 1024px) {
  .hero{
    height: 600px;
  }
  
  .hero-content {
    flex-direction: row;
  }

  .hero-text {
    margin-top: 100px;
    h1 {
      font-size: 70px;
    }
  }

  .features,
  .contact,
  .loan-types,
  .service,
  .faq {
    margin: 0;
    padding: 50px 0;
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

    p {
      font-size: 24px;
    }
  }

  .service .container {
    display: flex;
    align-items: center;
  }

  .service-image{
    width: 500px;
  }

  .service-text {
    text-align: left;
    margin-left: 60px;
    h2 {
      font-size: 50px;
    }
  }

  .service-description {
    margin: 30px 0;
    color: #6b6b6b;
  }

  .service-quality {
    display: grid;
    gap: 20px;
    grid-template-columns: auto auto;
  }

  .single-quality {
    display: flex;
    align-items: center;
  }

  .loan-types-title{
    font-size: 50px; 
    margin-bottom: 50px
  }

  .icon {
    width: 60px;
    height: 60px;
  }

  .faq-title{
    font-size: 50px;
    margin-bottom: 50px
  }

  .contact {
    height: 400px;
    display: flex;
    align-items: center;
    
    h2 {
      font-size: 86px;
    }
  }

  .carousel-slide {
    height: 350px;
    gap: 20px;

    a {
      border: 1px solid #625efd;
      border-radius: 20px;
      padding: 8px 20px;
      width: 140px;
    }
  }

  .slide-title{
    font-size: 20px;
  }

  .slide-description{
    font-size: 15px;
    flex-grow: 1;
  }
}
</style>
