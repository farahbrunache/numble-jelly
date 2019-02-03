<template>
  <div id="homepage-body">
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <p class="page-title">Numble Jelly</p>
    <p class="page-description">NFT Marketplace. Purchase sticker bundles on the blockchain.</p>
    <img src="../assets/homepage-thumbnail.png" alt="Thumbnail Picture 1" class="thumbnail">
    <router-link :to="{name: 'Shop'}">
      <button class="cta-button btn waves-effect waves-light deep-orange">Shop</button>
    </router-link>
  </div>
</template>
<script>
export default {
  name: 'Home'
};
</script>
<style scoped>
#homepage-body {
  background-image: url("../assets/background-image.jpg");
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  background-repeat: no-repeat;
  height: 100vh;
}
.page-title {
  font-family: "Abel", sans-serif !important;
  text-transform: uppercase;
  color: white;
  margin-left: 100px;
  font-size: 70px;
}
.page-title-2 {
  font-family: "Abel", sans-serif !important;
  text-transform: uppercase;
  color: white;
  margin-left: 100px;
  font-size: 70px;
}
.page-description {
  font-size: 20px;
  letter-spacing: 3px;
  margin-left: 100px;
  margin-top: 40px;
  color: white;
}
.cta-button {
  width: 170px;
  height: 56px;
  box-shadow: 0 19px 28px rgba(255, 46, 59, 0.42);
  background-color: #ff2e3b;
  margin-left: 100px;
  margin-top: -500px;
}
.thumbnail {
  margin-left: 600px;
  margin-bottom: 0;
}

/* Extra small devices (phones, 600px and down) */
@media only screen and (max-width: 600px) {
}

/* Small devices (portrait tablets and large phones, 600px and up) */
@media only screen and (min-width: 600px) {
}

/* Medium devices (landscape tablets, 768px and up) */
@media only screen and (min-width: 768px) {
}

/* Large devices (laptops/desktops, 992px and up) */
@media only screen and (min-width: 992px) {
}

/* Extra large devices (large laptops and desktops, 1200px and up) */
@media only screen and (min-width: 1200px) {
}
</style>
