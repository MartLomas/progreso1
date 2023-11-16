<script>
import bannerMobile from "../assets/image-hero-mobile.png";
import bannerDesktop from "../assets/image-hero-desktop.png";

import clientAudiophile from "../assets/client-audiophile.svg";
import clientDatabiz from "../assets/client-databiz.svg";
import clientMaker from "../assets/client-maker.svg";
import clientMeet from "../assets/client-meet.svg";

export default {
  data: function () {
    return {
      bannerMobile,
      bannerDesktop,
      clientLogos: [
        clientDatabiz,
        clientAudiophile,
        clientMeet,
        clientMaker,
      ]
    };
  },
};
</script>

<template>
  <section class="intro-section">
    <div class="banner-content">
      <img class="banner-mobile" :src="bannerMobile" alt="banner img">
      <img class="banner-desktop" :src="bannerDesktop" alt="banner img">
    </div>

    <div class="intro-info">
      <h1>Make remote work</h1>
      <p>
        Prepara tu trabajo para realizar la prueba de tercer progreso junto al profe de ingeniería web.
      </p>
      <button>Learn more</button>

      <div class="client-logo-content">
        <img :key="client" v-for="client in clientLogos" :src="client" alt="client logo">
      </div>
    </div>
  </section>
</template>

<style>
.banner-desktop {
  display: none;
}

.intro-section {
  display: flex;
  flex-direction: column;
  color: var(--medium-gray);
  font-weight: 200;
}

.banner-mobile {
  width: 100%;
  margin: 40px 0;
}

.intro-info {
  display: flex;
  flex-direction: column;
  text-align: center;
  box-sizing: border-box;
  padding: 0 20px;
}
.intro-info > * {
  margin: 0 0 20px 0;
}

.intro-info h1 {
  color: var(--almost-black);
  font-weight: bold;
  font-size: 2rem;
}

.intro-info button {
  margin: 0 auto;
  margin-bottom: 20px;
}

.client-logo-content {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
}

.client-logo-content img {
  margin: 5px;
}

@media (min-width: 1440px) {
  .banner-desktop {
    display: block;
    height: 70vh;
  }

  .banner-mobile {
    display: none;
  }

  .intro-section {
    flex-direction: row-reverse;
    justify-content: space-around;
    align-items: center;
    width: 80vw;
    margin: 0 auto;
    min-height: calc(100vh - 50px);
  }

  .intro-info {
    align-items: flex-start;
    max-width: 40%;
    text-align: left;
  }

  .intro-info h1 {
    font-size: 4rem;
  }

  .intro-info button {
    margin: 0 0 40px 0;
  }

  .intro-info > * {
    margin: 0 0 40px 0;
  }
}
</style>
