<template>
  <div>
    <header class="header">
      <div class="container flex-between">
        <div class="logo">
          <a href="#">
            <h1>Placko</h1>
          </a>
        </div>
        <nav class="main-navgation flex-between flex-ver-top">
          <div class="nav-links">
            <a href="#features"> </a>
          </div>
          <div class="nav-buttons">
            <a href="#" class="log-in"> </a>
            <a href="#" class="sign-up btn btn-sm" @click="launchPopup"
              >Launch Now</a
            >
          </div>
        </nav>
        <div class="burger-menu">
          <i class="fa-regular fa-bars icon"></i>
        </div>
      </div>
    </header>

        <div class="search">
          <vue-google-autocomplete
            ref="address"
            id="map"
            classname="form-control"
            placeholder="Please type your address"
            v-on:placechanged="getAddressData"
            country="us"
          >
          </vue-google-autocomplete>
          <button type="submit">
            <img src="../assets/search-image.png" alt="" class="search-icon">
          </button>
        </div>

    <div class="search-results">
      <div class="cards--">
          <div class="card--">
              <h1>Mumbai</h1>
              <h6>Several Species: Thermocol, or expanded polystyrene (EPS)</h6>
              <h6>Quantity : 12000 tonnes of waste</h6>
              <h6>Species affected : seabirds and sea turtles, seals and other marine mammals</h6>
          </div>
          <div class="card--">
              <h1>Kerala</h1>
              <h6>Several Species: leather products,medical waste(including syringes),fishing net and clothes</h6>
              <h6>Quantity : 1,057 tonnes of waste</h6>
              <h6>Species affected : Fish, seabirds, sea turtles, and marine mammals</h6>
          </div>
          <div class="card--">
            
          </div>
          
      </div>
    </div>
  </div>
</template>

<script>
  import VueGoogleAutocomplete from "vue-google-autocomplete";

  export default {
    components: { VueGoogleAutocomplete },

    data: function () {
      return {
        address: "",
      };
    },

    mounted() {
      // To demonstrate functionality of exposed component functions
      // Here we make focus on the user input
      this.$refs.address.focus();
    },

    methods: {
      /**
       * When the location found
       * @param {Object} addressData Data of the found location
       * @param {Object} placeResultData PlaceResult object
       * @param {String} id Input container ID
       */
      getAddressData: function (addressData) {
        this.address = addressData;
      },
    },
  };
</script>

<style lang="scss" scoped> 
  .search-results{
    padding:10px;
  }

  .cards-- {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    margin: 5px;
    .card-- {
        height: auto;
        padding: 10px;
        width: 70%;
        border-radius: 20px;
        background: rgb(169, 235, 240);
        margin: 15px;
        cursor: pointer;
        transition: all .3s;
        padding: 8px;
        justify-content: start;
        align-items: flex-start;
        h1 {
          font-size: 30px;
          padding:5px;
          font-weight: bold;
          color: #d7177b;
          text-decoration: underline;
        }
        h6 {
          font-size: 20px;
          padding: 12px;
          font-weight: 600;
          color: #4d4d4d;
        }
      }
  }

  
  
  .card--:hover{
      box-shadow: 0 0 10px grey;
  } 

  .search {
    display: flex;
    width: 60%;
    margin-left: 20%;
    margin-right: 20%;
    border-radius: 25px;
    border:1px solid black;
    padding: 8px;
    justify-content: space-between;

  }

  .search-icon {
    width:50px;
    height: 100%;
  }
  #map {
    padding:8px;
    width: 100%;
    border:none;
    outline: none;
    
  }

  a {
  text-decoration: none;
}
.landing-text {
  margin-bottom: 80px;
}
main {
  background-image: url("../assets/Bg.svg");
  height: 100vh;
  width: 100vw;
  overflow: hidden;
}
.btn {
  display: inline-block;
  color: white;
  background-color: #ec55c0;
  text-transform: capitalize;
  font-weight: 700;
  border: none;
  outline: none;
  cursor: pointer;
  border-radius: 100px;
  transition: 0.3s;
  background-image: linear-gradient(120deg, #f093fb 0%, #f5576c 100%);
  box-shadow: rgba(240, 46, 170, 0.4) -5px 5px,
    rgba(240, 46, 170, 0.3) -10px 10px, rgba(240, 46, 170, 0.2) -15px 15px,
    rgba(240, 46, 170, 0.1) -20px 20px, rgba(240, 46, 170, 0.05) -25px 25px;
}

.btn:active {
  box-shadow: none;
}

.btn.btn-sm {
  padding: 7px 21px;
}

.btn.btn-lg {
  padding: 16px 40px;
  font-size: 1.3rem;
  margin-left: 20px;
}
.flex-between {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 40px;
}

.flex-ver-top {
  align-items: flex-start;
}

.scale-effect:active {
  transform: scale(0.88);
  transition: 0.2s;
}

.section-header {
  text-align: center;
}

.chat-win {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 999;
}
.section-header h2 {
  font-size: 35px;
}

@media (max-width: 500px) {
  .section-header h2 {
    font-size: 26px;
  }
}

@media (max-width: 280px) {
  .section-header h2 {
    font-size: 22px;
  }
}

.section-header p {
  width: 50%;
  margin: 7px auto 0;
}

@media (max-width: 992px) {
  .section-header p {
    width: 70%;
  }
}

@media (max-width: 500px) {
  .section-header p {
    width: 100%;
  }
}

.container {
  position: relative;
  width: 78%;
  margin: 0 auto;
}

@media (max-width: 992px) {
  .container {
    width: 90%;
  }
}

.header {
  padding: 45px 0;
}

.header .logo h1 {
  font-size: 2.5rem;
  font-weight: 700;
  color: rgb(61, 61, 61);
}

.header .main-navgation {
  flex: 1;
  gap: 0;
}

@media (max-width: 992px) {
  .header .main-navgation {
    position: absolute;
    top: 150%;
    left: 50%;
    transform: translateX(-50%);
    width: 70%;
    height: 0;
    z-index: 999;
    overflow: hidden;
    flex-direction: column;
    align-items: center;
    padding: 0 33.33333px;
    border-radius: 10px;
    background-color: #3b3054;
    transition: height 0.3s;
  }
}

@media (max-width: 767px) {
  .header .main-navgation {
    width: 90%;
  }
}

@media (max-width: 375px) {
  .header .main-navgation {
    width: 100%;
  }
}

@media (max-width: 280px) {
  .header .main-navgation {
    padding: 0 25px;
  }
}

.header .main-navgation > div {
  display: flex;
  align-items: center;
  gap: 30px;
}

@media (max-width: 992px) {
  .header .main-navgation > div {
    flex-direction: column;
    width: 100%;
    padding: 33.33333px 0;
  }
}

@media (max-width: 280px) {
  .header .main-navgation > div {
    padding: 25px 0;
  }
}

.header .main-navgation div:first-child {
  border-bottom: 1px solid white;
}

.header .nav-buttons .btn {
  color: #fff;
  width: 80%;
}

@media (max-width: 375px) {
  .header .nav-buttons .btn {
    width: 100%;
  }
}

.header .burger-menu {
  font-size: 22px;
  color: #9e9aa7;
  cursor: pointer;
  display: none;
}

@media (max-width: 992px) {
  .header .burger-menu {
    display: block;
  }
}

.main-navgation a {
  font-weight: 700;
  font-size: 14px;
  color: #9e9aa7;
  transition: 0.3s;
}

.main-navgation a:hover {
  color: #232127;
}

@media (max-width: 992px) {
  .main-navgation a {
    width: 100%;
    color: white;
    text-align: center;
    font-size: 16px;
  }
  .main-navgation a:hover {
    color: #ec55c0;
  }
}

.landing {
  display: flex;
  align-items: center;
  padding: 5px 0;
  margin-left: 11%;
  overflow-x: hidden;
}

@media (max-width: 992px) {
  .landing {
    flex-direction: column-reverse;
    margin-left: 0;
    padding-bottom: 80px;
    row-gap: 60px;
  }
}

@media (max-width: 280px) {
  .landing {
    padding-bottom: 40px;
  }
}

.landing .landing-text {
  flex: 1;
  min-width: 465px;
}

@media (max-width: 992px) {
  .landing .landing-text {
    max-width: 95%;
    min-width: 0;
    text-align: center;
  }
}

.landing .landing-text h1 {
  width: 100%;
  font-size: 3.9em;
  line-height: 1.15;
  color: #ffffff;
  background: linear-gradient(to right, #4d4d4d 0, white 10%, #4d4d4d 20%);
  background-position: 0;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: shine 3s infinite linear;
  animation-fill-mode: forwards;
  -webkit-text-size-adjust: none;
  font-weight: 600;
  text-decoration: none;
  white-space: nowrap;
}

@keyframes shine {
  0% {
    background-position: 0;
  }
  60% {
    background-position: 470px;
  }
  100% {
    background-position: 470px;
  }
}

@media (max-width: 992px) {
  .landing .landing-text h1 {
    font-size: 3em;
  }
}

@media (max-width: 500px) {
  .landing .landing-text h1 {
    font-size: 2em;
  }
}

.landing .landing-text p {
  font-size: 18px;
  max-width: 500px;
  margin: 0 0 29.41176px;
}

@media (max-width: 992px) {
  .landing .landing-text p {
    font-size: 16px;
    margin: 10px auto 29.41176px;
  }
}

@media (max-width: 500px) {
  .landing .landing-text p {
    font-size: 15px;
  }
}

.landing .landing-image {
  position: relative;
  right: -70px;
}

@media (max-width: 992px) {
  .landing .landing-image {
    flex-basis: initial;
    right: -240px;
  }
}

@media (max-width: 767px) {
  .landing .landing-image {
    right: -170px;
  }
}

@media (max-width: 500px) {
  .landing .landing-image {
    right: -110px;
  }
}

@media (max-width: 375px) {
  .landing .landing-image {
    right: -120px;
  }
}

@media (max-width: 280px) {
  .landing .landing-image {
    right: -70px;
  }
}

@media (min-width: 1100px) {
  .landing .landing-image {
    right: -130px;
  }
}

.landing .landing-image img {
  width: 80%;
}



</style>
