<template>
  <div v-scroll="onScroll()">
    <HeaderComponent></HeaderComponent>
    <SliderComponent></SliderComponent>
    <div class="center">
      <MoviesComponent></MoviesComponent>
    </div>
    <FooterComponent></FooterComponent>
    <a href="#" class="back-to-top" v-if="isVisible"><i class="fa-solid fa-chevron-up"></i></a>
  </div>
</template>

<script>
import HeaderComponent from "./components/header/HeaderComponent.vue";
import SliderComponent from "./components/slider/Slider.vue";
import MoviesComponent from "./components/movies/Movies.vue";
import FooterComponent from "./components/footer/FooterComponent.vue";

export default {
  name: "App",
  data() {
    return {
      isVisible: false,
    };
  },
  components: {
    HeaderComponent,
    SliderComponent,
    MoviesComponent,
    FooterComponent,
  },
  created () {
    window.addEventListener('scroll', this.onScroll);
  },
  destroyed () {
    window.removeEventListener('scroll', this.onScroll);
  },
  methods: {
    onScroll() {
      this.isVisible = window.scrollY > 500
      console.log(this.isVisible)
    }
  }
};
</script>

<style>
@import "~@fortawesome/fontawesome-free/css/all.css";
@import "./assets/css/styles.css";

*{font-family: 'Quicksand', sans-serif;}

.back-to-top {
  position: fixed;
  right: 15px;
  bottom: 15px;
  z-index: 99999;
  text-decoration: none;
}

.back-to-top i {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  width: 40px;
  height: 40px;
  border-radius: 50px;
  background: #9352b3;
  color: #fff;
  transition: all 0.6s ease;
}

.back-to-top i:hover {
  background: #9352b3;
  color: #fff;
}


</style>
