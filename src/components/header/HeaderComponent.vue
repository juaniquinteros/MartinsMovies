<template>
  <header id="header">
    <div class="center">
      <nav class="navbar navbar-expand-lg bg-body-tertiary">
        <div class="container-fluid">
          <a class="logo" href="#"
            ><img src="../../assets/logo.svg" class="app-logo" alt="Logotipo"
          /></a>
          <button
            class="navbar-toggler"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav m-auto mb-2 mb-lg-0">
              <li class="nav-item dropdown">
                <a
                  class="nav-link dropdown-toggle"
                  href="#"
                  role="button"
                  data-bs-toggle="dropdown"
                  aria-expanded="false"
                >
                  Home
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="#">Home 1</a></li>
                  <li><a class="dropdown-item" href="#">Home 2</a></li>
                  <li><a class="dropdown-item" href="#">Home 3</a></li>
                  <li><a class="dropdown-item" href="#">Home 4</a></li>
                </ul>
              </li>
              <li class="nav-item dropdown">
                <a
                  class="nav-link dropdown-toggle"
                  href="#"
                  role="button"
                  data-bs-toggle="dropdown"
                  aria-expanded="false"
                >
                  Pages
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="#">404 Page</a></li>
                  <li><hr class="dropdown-divider" /></li>
                  <li>
                    <a class="dropdown-item" href="#">Celebrities List</a>
                  </li>
                  <li>
                    <a class="dropdown-item" href="#">Celebrities Grid</a>
                  </li>
                  <li>
                    <a class="dropdown-item" href="#">Celebrities Detail</a>
                  </li>
                  <li><hr class="dropdown-divider" /></li>
                  <li><a class="dropdown-item" href="#">Contact Us</a></li>
                  <li><a class="dropdown-item" href="#">Coming Soon</a></li>
                  <li><a class="dropdown-item" href="#">Pricing Plan</a></li>
                  <li>
                    <a class="dropdown-item" href="#">Login / Register</a>
                  </li>
                  <li><a class="dropdown-item" href="#">Testimonials</a></li>
                </ul>
              </li>
              <li class="nav-item dropdown">
                <a
                  class="nav-link dropdown-toggle"
                  href="#"
                  role="button"
                  data-bs-toggle="dropdown"
                  aria-expanded="false"
                >
                  Movies & TV Shows
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="#">Movie List 1</a></li>
                  <li><a class="dropdown-item" href="#">Movie List 2</a></li>
                  <li><a class="dropdown-item" href="#">Movie List 3</a></li>
                  <li><a class="dropdown-item" href="#">Movie List 4</a></li>
                  <li><a class="dropdown-item" href="#">Movie List 5</a></li>
                </ul>
              </li>
              <li class="nav-item dropdown">
                <a
                  class="nav-link dropdown-toggle"
                  href="#"
                  role="button"
                  data-bs-toggle="dropdown"
                  aria-expanded="false"
                >
                  Blog
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="#">Blog List</a></li>
                  <li><a class="dropdown-item" href="#">Blog Grid</a></li>
                  <li><a class="dropdown-item" href="#">Blog Detail</a></li>
                </ul>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Contact Us</a>
              </li>
            </ul>
            <div>
              <div class="d-flex">
                <div class="me-4">
                  <a class="nav-link margin-a" href="#" @click="openSearch()"
                    ><i class="fa-solid fa-magnifying-glass"></i
                  ></a>
                </div>
                <div class="position-relative me-4 margin-a">
                  <i class="fa-solid fa-earth-americas"></i>
                  <span
                    class="
                      position-absolute
                      top-0
                      start-100
                      translate-middle
                      badge
                      rounded-pill
                      bg-danger
                    "
                  >
                    2
                    <span class="visually-hidden">unread messages</span>
                  </span>
                </div>
                <button class="btn btn-purple btn-login">
                  <i class="fa-regular fa-user"></i>
                  <span>LOGIN</span>
                </button>
              </div>
            </div>
          </div>
        </div>
      </nav>

      
    </div>
    <div :class="open ? 'open search' : 'search'">
        <form class="search-form" role="search" action="#">
          <input type="text" placeholder="Type and hit enter" @change="search($event.target.value)">
          <span id="close" class="togle-search" @click="openSearch()"><i class="fa-solid fa-xmark"></i></span>
        </form>
      </div>
  </header>
</template>

<script>
import axios from "axios"; 
export default {
  name: "HeaderComponent",
  data() {
    return {
      open: false
    };
  },
  mounted() {
  },
  methods: {
    async search(keywords){
      let keywordsFormatted  = keywords.replace(/\s+/g, '%20')
       axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=1e448e0dfcdbb565f5d329820065b4d2&query=${keywordsFormatted}&page=1`
        )
        .then((res) => {
          this.$store.commit("setMovies", res.data.results);
        }); 
    },

    openSearch() {
      this.open = !this.open
    }
   }
};
</script>

<style>
.center {
  position: relative;
}

.logo {
  width: 150px;
}

.margin-a {
    margin-top: 5px;
}

.badge {
    font-size: 9px;
    margin-top: 5px;
}

.btn-login i{
    font-size: 12px;
    margin-right: 10px;
}
nav {
  margin: 8px 16px
}

.search {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  z-index: 99;
  height: 60px;
  background: white;
  padding: 0 20px;
  transition: all 0.5s ease;
  opacity: 0;
  visibility: hidden;
}

.open{
  opacity: 1;
  visibility: visible;
}

.search .search-form {
  position: relative;
}

.search .search-form input {
  height: 70px;
  border: 0;
  font-size: 20px;
  width: 100%;
  padding: 10px 20px;
  color: #666;
  appearance: none;
}

.search .search-form input:focus {
  outline: none;
}

.search .search-form .togle-search {
  position: absolute;
  right: 15px;
  top: 8px;
  line-height: 60px;
  cursor: pointer;
  color: #666;
  font-size: 18px;
}
</style>
