<template>
  <h2>Links</h2>
  <div class="social-links">
    <a
      v-for="link in socialLinks"
      :key="link.name"
      :href="link.url"
      target="_blank"
      rel="noopener noreferrer"
      :aria-label="link.name"
    >
      <font-awesome-icon
        v-if="link.icon"
        :icon="link.icon"
        aria-hidden="true"
      />
      <svg v-else viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
        <path
          d="M3 9l3-3 3 3-3 3-3-3zm6 6l3-3 3 3-3 3-3-3zm6-6l3-3 3 3-3 3-3-3z"
        />
      </svg>
      <span class="sr-only">{{ link.name }}</span>
    </a>
  </div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import {
  faFacebookF,
  faInstagram,
  faYoutube,
  faSpotify,
  faItunesNote,
} from "@fortawesome/free-brands-svg-icons";
import { faEnvelope } from "@fortawesome/free-solid-svg-icons";

// Lisää ikonit FontAwesome-kirjastoon
library.add(
  faFacebookF,
  faInstagram,
  faYoutube,
  faSpotify,
  faItunesNote,
  faEnvelope
);

export default {
  name: "SocialLinks",
  components: {
    FontAwesomeIcon,
  },
  data() {
    return {
      socialLinks: [
        {
          name: "Instagram",
          url: "https://www.instagram.com/shakalsband/",
          icon: ["fab", "instagram"],
        },
        {
          name: "Facebook",
          url: "https://www.facebook.com/shakalsofficial/",
          icon: ["fab", "facebook-f"],
        },
        {
          name: "Spotify",
          url: "https://open.spotify.com/artist/5m0S1SzGV5zxUGgTqbrt2F?si=eyiLRN_yRYaniEE-FasVdQ",
          icon: ["fab", "spotify"],
        },
        {
          name: "iTunes",
          url: "https://itunes.apple.com/us/artist/shakals/965090596",
          icon: ["fab", "itunes-note"],
        },
        {
          name: "Tidal",
          url: "https://tidal.com/browse/artist/24054615",
          icon: null, // Käytetään SVG:tä, koska FontAwesome ei tue Tidal-ikonia
        },
        {
          name: "YouTube",
          url: "https://www.youtube.com/channel/UC4fnV8qaZRGhb-gfAxLVaNQ",
          icon: ["fab", "youtube"],
        },
        {
          name: "Email",
          url: "mailto:management@shakals.com",
          icon: ["fas", "envelope"],
        },
      ],
    };
  },
};
</script>

<style scoped>
.social-links {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  justify-content: left;
}

.social-links a {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 50px;
  height: 50px;
  background-color: var(--vt-c-black-soft);
  border-radius: 50%;
  transition: background 0.3s ease-in-out;
  font-size: 20px;
  color: var(--vt-c-white);
  position: relative;
  text-decoration: none;
  flex-shrink: 0;
  aspect-ratio: 1 / 1;
}

.social-links a:hover {
  background-color: var(--primary);
}

.social-links a:focus {
  outline: 2px solid var(--accent);
  outline-offset: 2px;
}

/* SVG-ikonin tyylit */
svg {
  width: 25px;
  height: 25px;
  fill: var(--vt-c-white);
}

/* Piilotettu teksti ruudunlukijoille */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
</style>
