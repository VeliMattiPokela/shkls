<template>
  <div class="container">
    <h2 aria-label="Upcoming gigs section">Upcoming gigs</h2>

    <div v-if="upcomingGigs.length > 0">
      <div v-for="item in upcomingGigs" :key="item.date">
        <p>
          <strong>
            {{ item.date }} {{ item.venue }}, {{ item.city }}
            <span v-if="item.with.length > 0">(+ {{ item.with }})</span>
          </strong>
        </p>
        <p v-if="item.info.length > 0">
          <a :href="item.info" target="_blank" rel="noopener noreferrer">
            More info
          </a>
        </p>
      </div>
    </div>
    <p v-else class="no-shows" aria-live="polite">No upcoming gigs announced</p>

    <h3 class="mt-lg" aria-label="Past gigs section">Past gigs</h3>

    <div v-for="item in pastGigs" :key="item.date">
      <p class="muted">
        {{ item.date }} {{ item.venue }}, {{ item.city }}
        <span v-if="item.with.length > 0">(+ {{ item.with }})</span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Bio",
  data() {
    return {
      today: new Date(), // Tänään Date-objektina
      gigs: [
        {
          date: "25.01.2025",
          venue: "Tavastia",
          city: "Helsinki",
          with: "Moon Shot",
          info: "",
        },
        {
          date: "24.01.2025",
          venue: "Olympia",
          city: "Tampere",
          with: "Moon Shot",
          info: "",
        },
        {
          date: "06.11.2024",
          venue: "On The Rocks",
          city: "Helsinki",
          with: "Get In",
          info: "",
        },
        {
          date: "11.01.2020",
          venue: "Semifinal",
          city: "Helsinki",
          with: "Deepwater",
          info: "https://www.facebook.com/events/592163524536597/",
        },
        {
          date: "28.12.2019",
          venue: "Toppila Klubi",
          city: "Oulu",
          with: "",
          info: "",
        },
        {
          date: "07.11.2019",
          venue: "Bar Loose",
          city: "Helsinki",
          with: "Messier, Survive the Silence",
          info: "https://www.facebook.com/events/592163524536597/",
        },
        {
          date: "09.11.2018",
          venue: "Jack The Rooster",
          city: "Tampere",
          with: "Sadetta",
          info: "https://www.facebook.com/events/592163524536597/",
        },
        {
          date: "02.05.2018",
          venue: "Lepakkomies",
          city: "Helsinki",
          with: "Cyril Awakens",
          info: "",
        },
        {
          date: "10.01.2018",
          venue: "Bar Loose",
          city: "Helsinki",
          with: "The Stoats, New Fashioned",
          info: "",
        },
        {
          date: "28.10.2017",
          venue: "Hyvän Mielen Rock",
          city: "Loviisa",
          with: "Varvara, etc.",
          info: "",
        },
        {
          date: "12.10.2017",
          venue: "Elmun Baari",
          city: "Helsinki",
          with: "Superbeat, Cyril Awakens",
          info: "",
        },
        {
          date: "12.07.2017",
          venue: "Lepakkomies",
          city: "Helsinki",
          with: "Varvara, etc.",
          info: "",
        },
        {
          date: "17.06.2017",
          venue: "Hoi Sie Galleria",
          city: "Lappeenranta",
          with: "Varvara, etc.",
          info: "",
        },
      ],
    };
  },
  computed: {
    upcomingGigs() {
      return this.gigs.filter(
        (item) => this.parseDate(item.date) >= this.today
      );
    },
    pastGigs() {
      return this.gigs.filter((item) => this.parseDate(item.date) < this.today);
    },
  },
  methods: {
    // Muuntaa dd.mm.yyyy -> Date-objektiksi
    parseDate(dateStr) {
      const [day, month, year] = dateStr.split(".").map(Number);
      return new Date(year, month - 1, day);
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 800px; /* Rajaa sisällön enimmäisleveyttä */
  margin-left: auto; /* Keskittää sisällön */
  margin-right: auto; /* Keskittää sisällön */
}
.muted {
  color: var(--muted);
}

.no-shows {
  color: var(--muted);
}
</style>
