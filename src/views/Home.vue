<template>
  <div class="home">
    <AppLoader v-if="loading"/>
    <h1 class="home__heading">{{data.name}}</h1>
    <div class="home__section home__section--left"></div>
    <div class="home__section home__section--right"></div>
    <img
      src="../assets/image3.jpg"
      alt="Aquila Aveion Image"
      class="home__image"
    />
    <div class="home__footer">
      <p class="home__link">HOME</p>
      <p class="home__link">ABOUT</p>
      <img
        src="../assets/image3.jpg"
        alt="Aquila Aveion Image"
        class="home__link--image"
      />
      <p class="home__link">GALLERY</p>
      <p class="home__link">CONTACT</p>
    </div>
    <div class="home__side-bar">
      <a :href="`https://instagram.com/${data.social_media.instagram}`" target="_blank"
        ><img
          src="../assets/instagram.svg"
          alt="Instagram Icon"
          class="home__icon"
      /></a>
      <a :href="`https://twitter.com/${data.social_media.twitter}`" target="_blank">
        <img src="../assets/twitter.svg" alt="Twitter Icon" class="home__icon"
      /></a>
      <a :href="`https://snapchat.com/${data.social_media.snapchat}`" target="_blank">
        <img src="../assets/snapchat.svg" alt="Snapchat Icon" class="home__icon"
      /></a>
      <a :href="`mailto: ${data.social_media.email}`" target="_blank">
        <img src="../assets/mail.svg" alt="Mail Icon" class="home__icon"
      /></a>
    </div>
  </div>
</template>

<script>
import AppLoader from "../components/AppLoader"
export default {
  components: {
    AppLoader
  },
  name: "Home",
  data() {
    return {
     data: {
       social_media: {}
     },
     loading: false
    };
  },

  mounted() {
    this.fetchData();
  },
  methods: {
   fetchData() {
     this.loading = true
      const baseUrl = 'https://hirng-x2021.glitch.me/api'
         this.$http.get(baseUrl)
      .then((response) => {
       this.data = response.data
       this.loading = false
      })
        .catch((error) => {
         this.loading = false
        });
    },
  },
};
</script>
