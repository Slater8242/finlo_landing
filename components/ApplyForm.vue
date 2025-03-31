<script setup lang="ts">
const isTerritory = ref(false);
const realEstateOptionValue = ref("apartment");
const newsChecbox = ref(true);
const termsCheckbox = ref(true);
const formData = ref<Record<string, string | number>>({
  name: "",
  lastname: "",
  email: "",
  phone: "",
  personalCode: "",
  loanAmount: "",
  loanPurpose: "Kredītu apvienošana",
  realEstateType: "apartment",
  city: "",
  street: "",
  district: "",
  cadastralNumber: ""
});


const handleSubmit = () => {
  console.log("Submitted form data:", formData.value);
  alert("Dati nosūtīti!");
};

watch(realEstateOptionValue, (newValue) => {
  isTerritory.value = newValue === "land" || newValue === "forest";
  formData.value.realEstateType = newValue;  
});

const borrowerInputs = [
  {name:"name", placeholder:"Vārds"},
  {name:"lastname", placeholder:"Uzvārds"},
  {name:"email", placeholder:"E-pasts"},
  {name:"phone", placeholder:"Tālrunis"},
  {name:"personalCode", placeholder:"Personas kods"},
]

const loanPurposeOptions =[
  "Kredītu apvienošana",
  "Biznesam",
  "Zemniekiem",
  "Ēku būvniecībai",
  "Hipotekārais kredīts",
]

const realEstateOptions = [
  {value:"apartment", label:"Dzīvoklis"},
  {value:"house", label:"Māja"},
  {value:"land", label:"Zeme"},
  {value:"commercial", label:"Komercobjekts"},
  {value:"forest", label:"Mežs"},
]

</script>

<template>
  <form @submit.prevent="handleSubmit">
    <h3 class="title">Informācija par aizņēmēju</h3>
    <div class="borrower-info">
      <input class="input-styling"
        v-for="(borrowerInput, index) in borrowerInputs" 
        v-model="formData[borrowerInput.name]"
        type="text" 
        :placeholder="borrowerInput.placeholder+'*'" 
        :key="index" 
        required
      >
    </div>
    <h3 class="title">Aizdevuma mērķis</h3>
    <div class="loan-purpose">
      <input type="number" placeholder="Nepieciešamā summa*" class="input-styling" v-model="formData.loanAmount" required>
      <select name="purpose" id="purpose" class="input-styling" v-model="formData.loanPurpose">
        <option v-for="(option, index) in loanPurposeOptions" :value="option" :key="index">{{ option }}</option>
      </select>
    </div>
    <h3 class="title">Informācija par nekustamo īpašumu</h3>
    <div class="real-estate-info">
      <select name="real-estate" id="real-estate" class="input-styling" v-model="realEstateOptionValue">
        <option v-for="(option, index) in realEstateOptions" :value="option.value" :key="index">{{ option.label }}</option>
      </select>
      <input v-if="!isTerritory" type="text" placeholder="Pilsēta*" class="input-styling" v-model="formData.city">
      <input v-if="!isTerritory" type="text" placeholder="Iela / Nr*" class="input-styling" v-model="formData.street">
      <input v-if="isTerritory" type="text" placeholder="Rajons" class="input-styling is-territory" v-model="formData.district">
      <input v-if="isTerritory" type="text" placeholder="Kadastra numurs vai zemes nosaukums" class="input-styling is-territory" v-model="formData.cadastralNumber">
    </div>

    <Checkbox v-model="newsChecbox" label="Piekrītu saņemt jaunumus no FINLO savā e-pastā."/>
    <Checkbox v-model="termsCheckbox" label="Es apstiprinu, ka esmu izlasījis un piekrītu vietnes Privātuma politika / noteikumi.*" style="margin: 20px 0;"/>
    <Button label="Apstiprināt" type="submit"/>
  </form>
</template>

<style scoped>
form{
  color: #000;
}

.title{
  margin: 20px 0;
}

.borrower-info, .loan-purpose, .real-estate-info{
  display: grid;
  grid-template-columns: auto;
  gap: 15px;
}

.real-estate-info{
  margin-bottom: 40px;
}

.input-styling{
  padding: 10px;
  height: 25px;
  border: 1px solid #e5e7eb;
  border-radius: 10px;
}

@media only screen and (min-width: 1024px) {
  .borrower-info, .loan-purpose, .real-estate-info{
    grid-template-columns: auto auto;
  }

  .borrower-info input:last-child, .real-estate-info select, .is-territory{
    grid-column: span 2;
  }

  .input-styling{
    height: 40px;
  }
}

</style>