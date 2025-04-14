<script setup>
import {useRoute} from 'vue-router'

const popupOpen = ref(false);

// Access the dynamic parameter (slug) from the route
const route = useRoute()
const slug = route.params.slug

// Define your content (could also be fetched from an API, static file, etc.)
const services = {
  "mortgage-loan": {
    title: "Hipotekārais kredīts",
    description1: "Aizdevums ar nekustamā īpašuma ķīlas nodrošinājumu. Īpašuma iegādei, esoša aizdevuma pārkreditācijai vai esoša īpašuma ieķīlāšana.",
    description2: "Kredīts pret nekustamā īpašuma ķīlu ir piemērots risinājums fiziskām vai juridiskām personām, kurām pieder nekustamais īpašums, tas ir ilgtermiņa darījums, kas tiek nodrošināts ar nekustamā īpašuma ķīlu. Kredīts klientam tiek piešķirts līdz pat 75% apmērā no ķīlas vērtības un tiek izsniegts personām, kuras sasniegušas vismaz 18 gadu vecumu."
  },
  "business-loan": {
    title: "Biznesa attīstībai",
    description1: "Esošajiem vai topošajiem saimnieciskās darbības veicējiem apgrozāmajiem līdzekļiem, darba materiālu/tehnikas iegādei vai uzņēmējdarbības uzsākšanai.",
    description2: "Kredīts biznesam ir piemērots risinājums pašnodarbinātām personām, kuras plāno uzsākt vai veic saimniecisko darbību, zemnieku saimniecībām, kā arī uzņēmējiem, kuriem nepieciešami apgrozāmie līdzekļi. Kredīts tiek izsniegts tikai ar nekustamā īpašuma nodrošinājumu."
  },
  "construction-loan": {
    title: 'Ēku būvniecībai',
    description1: 'Kredīts būvniecībai galvenokārt ir piemērots risinājums būvniekiem un nekustamo īpašumu attīstītājiem, bet ne retums šo kredīta veidu izvēlās arī mājsaimniecības.',
    description2: "Kredīts pret nekustamā īpašuma ķīlu būvniekiem vai sava nekustamā īpašuma būvniecībai. Atrast finanšu partneri biznesa projektiem var šķist sarežģīti un izaicinošu."
  },
  "loan-consolidation": {
    title: 'Kredītu apvienošana',
    description1: 'Apvienojot kredītus iespējams ietaupīt laiku un naudu, jo maksājumu turpmāk veiksi pie viena aizdevēja. Lai saņemtu piedāvājumu no mums – aizpildi pieteikumu.',
    description2: "Kredītu apvienošana ir piemērots risinājums, ja vēlaties, lai tiktu pārskatītas esošo aizdevumu procentu likmes un samazinātos Jūsu ikmēneša maksājumu apmērs. Visus kredītus apvienojot vienā, tiek nokārtotas saistības ar esošajiem kreditoriem, kā rezultātā turpmāk maksājumi veicami pie viena aizdevēja."
  },
  "farm-loan": {
    title: 'Zemniekiem',
    description1: 'Zemnieku saimniecībām apgrozāmajiem līdzekļiem, tehnikas iegādei vai remontam, izejmateriālu iegādei.',
    description2: "Kredīts pret nekstamā īpašuma ķīlu zemniekiem, zemnieku saimniecībām vai piemājas saimniecībām vairumā gadījumu izvēlas, lai veikto esošā kredīta pārfinansēšanu uz izdevīgākiem nosacījumiem vai lai attīstītu, uzlabotu vai paplašinātu savu saimniecību. Aizdevumu pret zemes vai meža ķīlu vairumā gadījumu izvēlas zemnieku saimniecību pārstāvji, kā arī personas piemājas saimniecībām."
  }
}

// Get the content based on the slug
const serviceContent = services[slug] || {title: 'Service Not Found', content: 'Sorry, this service does not exist.'}

const applySteps = [
  "Aizpildi pieteikumu un saņem piedāvājumu e-pastā",
  "Apstiprini līgumu ar elektronisko parakstu vai saņem to ar kurjeru",
  "Saņem aizdevumu savā kontā un novirzi to plānotajam mērķim"
];

const features = [
  {title: "Licencēts aizdevējs", icon: "mdi:certificate"},
  {title: "NĪ nodrošināti kredīti", icon: "mdi:home-lock"},
  {title: "Tirgū no 2008. gada", icon: "mdi:calendar-check"},
];

const accordionItems = [
  {
    title: "Vai iespējams kredītu atdot ātrāk?",
    content: "Jā, kredītu pirms termiņa iespējams atdot ātrāk.",
  },
  {
    title: "Vai daļu kredīta iespējams saņemt uzreiz?",
    content: "Steidzamu biznesa jautājumu risināšanai, varam izvērtēt daļu finansējuma izsniegt līguma parakstīšanas dienā.",
  },
  {
    title: "Vai tiks pārbaudīts kredīta izmantošanas mērķis?",
    content: "Mēs aicināsim Jūs mūs informēt par kredīta izmantošanas mērķi.",
  },
]
</script>

<template>
  <section class="service-title">
    <div class="container">
      <h1 class="title">{{ serviceContent.title }}</h1>
    </div>
  </section>

  <section class="service-description">
    <div class="container description">
      <p class="description-text">
        {{ serviceContent.description1 }}
      </p>
      <Button label="Pieteikties" @click="popupOpen = true" />
      <Popup :show="popupOpen" @close="popupOpen = false">
        <ApplyForm />
      </Popup>
    </div>
  </section>

  <section class="features">
    <div class="container">
      <h1 class="title">Par mums</h1>
      <div class="feature-grid">
        <div class="feature-card" v-for="feature in features">
          <Icon :name="feature.icon" class="icon"/>
          <p>{{ feature.title }}</p>
        </div>
      </div>
    </div>
  </section>

  <section class="apply-steps">
    <div class="container">
      <h1 class="title">Kā pieteikties?</h1>
      <div class="steps">
        <div class="step" v-for="(step,index) in applySteps" :key="index">
          <span class="step-number">
            {{ `${index + 1}` }}
          </span>
          <span class="step-description">
            {{ step }}
          </span>
          <div v-if="index < applySteps.length - 1" class="step-divider"></div>
        </div>
      </div>
      <Button label="Pieteikties" @click="popupOpen = true" />
    </div>
  </section>

  <section class="service-description">
    <div class="container description">
      <p class="description-text2">
        {{ serviceContent.description2 }}
      </p>
    </div>
  </section>

  <section class="faq" id="faq">
    <div class="container">
      <h1 class="title">Biežāk uzdotie jautājumi</h1>
      <Accordion :items="accordionItems" />
    </div>
  </section>

  <section class="contact">
    <div class="container">
      <h2>Sazinies ar mums</h2>
      <a href="tel:+37167199909">67 19 99 09</a>
    </div>
  </section>
</template>

<style scoped>
section {
  padding: 30px 0;
}

.service-title {
  background-color: #f1f0ff;
  background-image: url("@/assets/images/transparent_bg.png");
  background-size: cover;
  background-repeat: no-repeat;
  color: #fff;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  padding: 50px 0;
}

.service-title .title {
  color: #000;
}

.title {
  font-size: 30px;
  text-align: center;
  margin-bottom: 30px;
}

.icon {
  width: 40px;
  height: 40px;
  color: #6a47ed;
}

.description {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.description-text {
  font-size: 20px;
  padding: 30px 0;
}

.description-text2 {
  font-size: 15px;
}

.features {
  position: relative;
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

.apply-steps .container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.steps {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 30px;
  margin-bottom: 50px;
}

.step {
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 30px;
  text-align: center;
}

.step-number {
  font-size: 50px;
}

.step-divider {
  width: 2px;
  height: 40px; /* Line thickness */
  background-color: #000; /* Line color */
}

.contact {
  text-align: center;
  color: #fff;
  font-size: 21px;
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
    text-decoration: none;
  }
}

@media only screen and (min-width: 768px) {
  .feature-grid {
    grid-template-columns: auto auto;
  }

  .service-title {
    padding: 150px 0;
  }

  .feature-card:last-child{
    grid-column: 1 / span 2;
  }
}

@media only screen and (min-width: 1024px) {
  section {
    padding: 80px 0;
  }

  .icon {
    width: 60px;
    height: 60px;
  }

  .title {
    font-size: 70px;
    text-align: center;
    margin-bottom: 50px;
  }

  .service-title .title {
    margin: 0;
  }

  .description-text {
    padding: 75px 0;
    font-size: 30px;
  }

  .description-text2{
    padding: 75px 0;
    font-size: 20px;
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
    gap: 30px;

    p {
      font-size: 24px;
    }
  }

  .steps {
    flex-direction: row;
  }

  .step {
    flex-direction: row;
  }

  .step-number {
    font-size: 100px;
  }

  .step-description {
    font-size: 15px;
  }

  .step-divider {
    width: 80px;
    height: 2px; /* Line thickness */
    background-color: #000; /* Line color */
  }

  .contact {
    height: 400px;
    display: flex;
    align-items: center;
    font-size: 30px;
    h2 {
      font-size: 86px;
    }
  }
}
</style>
