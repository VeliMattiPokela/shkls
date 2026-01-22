<script setup>
import Links from "./Links.vue";
</script>

<template>
  <div class="container">
    <img
      class="promo-image mb-lg"
      src="../assets/shakals-promo-lowres.0aa7abc.jpg"
      alt="Shakals promo"
    />
    <h1>Shakals</h1>
    <p>
      Brewed in a construction site hut in Southern Finland, the sound of
      Shakals is a unique combination of streetwise indie rock and ominous
      electro features. The group was formed in 2014 for intense studio
      lock-ins, which gave rise to hours of new material that became their
      foundation.
    </p>
    <p>
      With a discography reaching from disco-oriented bangers to soulful indie
      tunes, the band's sound from vocals to instrumentation remains
      recognisable.
    </p>
    <p>
      Bookings:
      <a href="mailto:management@shakals.com">management@shakals.com</a>
    </p>
    <Links />
  </div>
</template>

<style scoped>
.container {
  max-width: 800px; /* Rajaa sisällön enimmäisleveyttä */
  margin-left: auto; /* Keskittää sisällön */
  margin-right: auto; /* Keskittää sisällön */
}

.promo-image {
  width: 100%; /* Skaalaa kuvan leveyden mukautumaan konttiin */
  max-width: 800px; /* Estää kuvan venymisen liian leveäksi */
  height: auto; /* Säilyttää mittasuhteet */
}

@media (max-width: 768px) {
  .promo-image {
    max-width: 100%; /* Varmistaa, että kuva ei ole liian iso mobiilissa */
    border-radius: 4px; /* Vähentää kulmien pyöristystä pienemmillä näytöillä */
  }
}
</style>
