<template>
  <div class="slider">
    <div class="container">
      <div class="inner">
        <h1>Movies</h1>
        <div class="text">
          <a href="#" class="btn-home">Home</a>
          <span class="line">|</span>
          <span class="text-2">Movie Grid</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SliderComponent",
};
</script>

<style>
.slider{
  background: url('../../assets/movie-collection.jpg');
  position: relative;
  padding: 50px 0;
}

.slider:before {
  content: "";
  position: absolute;
  display: block;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to bottom, #a11f3c 0%, #8240a3 100%);
  opacity: .7;
}

.slider:after {
  content: "";
  position: absolute;
  display: block;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: .6;
}

.slider .inner {
  position: relative;
  z-index: 10;
}

.slider .inner h1{
  color:white;
  font-weight: 400;
  font-size: 38px;
  margin: 0;
  padding: 0;
  text-transform: capitalize;
}
.slider .inner text {
  font-size: 25px;
}

.slider .inner a {
  text-decoration: none;
  color: white;
  font-size: 20px;
} 

.slider .inner .line{
  padding: 0 10px 0 16px;
  color: white
}

.slider .inner .text-2 {
  color: #b3bbce;
}

</style>