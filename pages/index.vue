<script setup lang="ts">

</script>

<template>
  <div class="content">
    <section class="hero">
      <div class="container">
        <div class="hero-content">
          <h2>Mūsdienīga pieeja <br>
            Aizdevumu izsniegšanai</h2>
          <p>
            Finlo darbības virziens ir aizdevumu izsniegšana ar nekustamā īpašuma nodrošinājumu jeb hipotekārais kredīts.
            <br>
            Izprotot klientu vēlmes un vajadzības, esam izstrādājuši pieteikšanās un kredīta izvērtēšanas procedūru pēc iespējas ērtāku un klientam piemērotāku.
          </p>
          <button class="cta-button">Get Started</button>
        </div>
      </div>
    </section>

    <section class="about">
      <div class="container">
        <h2>Why Choose Us?</h2>
        <p>We provide seamless financial services with top-tier security and convenience.</p>
      </div>
    </section>

    <section class="features">
      <div class="container">
        <h2>Our Features</h2>
        <div class="feature-grid">
          <div class="feature-card">
            <h3>🔒 Secure Transactions</h3>
            <p>End-to-end encryption for safe payments.</p>
          </div>
          <div class="feature-card">
            <h3>⚡ Instant Transfers</h3>
            <p>Send and receive money within seconds.</p>
          </div>
          <div class="feature-card">
            <h3>📞 24/7 Support</h3>
            <p>Always here to help, anytime you need.</p>
          </div>
          <div class="feature-card">
            <h3>⚡ Instant Transfers</h3>
            <p>Send and receive money within seconds.</p>
          </div>
          <div class="feature-card">
            <h3>📞 24/7 Support</h3>
            <p>Always here to help, anytime you need.</p>
          </div>
          <div class="feature-card contact-card">
            <h3>📞 Need more info?</h3>
            <p>Contact us now!</p>
          </div>
        </div>
      </div>
    </section>

    <section class="contact">
      <div class="container">
        <h2>Contact Us</h2>
        <p>Email: support@fintechpro.com</p>
      </div>
    </section>
  </div>
</template>

<style scoped>

@media only screen and (min-width: 1280px){
  .content{
    padding-top: 100px;
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
    padding: 60px 20px;
    background: #574D93;
    color: white;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    z-index: 0;
  }

  .hero-content{
    display: flex;
    row-gap: 30px;
    align-items: center;
    flex-direction: column;
  }

  .about, .features, .contact {
    position: relative;
    margin-top: 30px;
    padding: 40px 20px;
  }

  .hero::before{
    display: block;
    content: "";
    top: 0;
    left: 0;
    position: absolute;
    width: 50%;
    height: 100%;
    background-image: url("@/assets/images/man.png");
    background-repeat: no-repeat;
    background-size: contain;
    background-position: center;
    z-index: -1;
  }

  .features::before{
    display: block;
    content: "";
    bottom: 50px;
    right: 0;
    position: absolute;
    width: 55%;
    height: 115%;
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
    grid-template-columns: auto auto auto;
    justify-content: space-between;
    gap: 20px;
    margin-top: 30px;
  }

  .feature-card {
    width: 240px;
    height: 80px;
    background: rgba(255, 255, 255, 0.3);
    padding: 35px 20px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    flex: 1;
    text-align: center;
  }

  .contact-card{
    background-color: rgba(38, 31, 179, 0.5);
  }

  .contact{
    background-color: #8C92A6;
  }
}
</style>