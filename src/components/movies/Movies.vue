<template>
  <div class="body">
    <div class="container">
      <div class="row mb-5">
        <div class="col-md-6">
          <button class="btn btn-grey me-3">
            <i class="fa-solid fa-bars"></i>
          </button>
          <button class="btn btn-grey active">
            <i class="fa-solid fa-grip"></i>
          </button>
        </div>
        <div class="text-end col-md-6">
          <div class="w-select">
            <select class="filter" name="" id="">
            <option value="">Default Order</option>
            <option value="">Features</option>
            <option value="">Top Viewed</option>
            <option value="">Top Rated</option>
            <option value="">Newest</option>
            <option value="">Oldest</option>
            </select>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-lg-4 col-md-6 col-sm-12" v-for="movie in movies" v-bind:key="movie.id">
          <div class="card">
            <div class="image-content">
                <div class="button">
                    <a class="like" href="#" data-bs-toggle="tooltip" data-bs-placement="bottom" data-bs-title="Rate">
                        <i class="fa-regular fa-heart"></i>
                    </a>
                    <a class="share" href="#" data-bs-toggle="tooltip" data-bs-placement="bottom" data-bs-title="Rate">
                        <i class="fa-solid fa-share-nodes"></i>
                    </a>
                </div>
                <div class="stars">
                    <div class="rating">
                        <i :class="movie.vote_average/2 > 1 ? 'fa-solid fa-star' : 'fa-regular fa-star' "></i>
                        <i :class="movie.vote_average/2 > 2 ? 'fa-solid fa-star' : 'fa-regular fa-star' "></i>
                        <i :class="movie.vote_average/2 > 3 ? 'fa-solid fa-star' : 'fa-regular fa-star' "></i>
                        <i :class="movie.vote_average/2 > 4 ? 'fa-solid fa-star' : 'fa-regular fa-star' "></i>
                        <i :class="movie.vote_average/2 > 5 ? 'fa-solid fa-star' : 'fa-regular fa-star' "></i>
                    </div>
                </div>
                <div class="watched">
                  <span class="badge rounded-pill watched-text" v-if="ids ? ids.includes(movie.id) : ''">Watched</span>
                </div>
                <div class="play">
                    <a class="video" @click="watch(movie.id)" href="#"><i class="fa-solid fa-play"></i></a>
                </div>
                <img class="card-img-top" :src="movie.poster_path == null ? 'https://i.pinimg.com/736x/4e/4f/3e/4e4f3e3dd16bc08db85531b0294138b7.jpg' : 'https://image.tmdb.org/t/p/w500'+movie.poster_path" :alt="movie.original_title" />
            </div>
            <div class="card-body">
              <h5 class="card-title">{{ movie.original_title }}</h5>
              <p class="card-text">{{ movie.overview }}</p>
              <a @click="imdb(movie.id)" class="btn btn-purple btn-float">Read more</a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <nav>
      <ul class="pagination justify-content-center">
        <li><a class="current-page" href="#">1</a></li>
        <li><a href="#">2</a></li>
        <li><a href="#">3</a></li>
        <li>
          <a href="#" aria-label="Next">
            <span aria-hidden="true"
              ><i class="fa-solid fa-chevron-right"></i
            ></span>
          </a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "MoviesComponent",
  data() {
    return {
      movies: [],
      moviesDetailed: [],
      historyWatchedMovies: [],
      ids: [],
    };
  },
  watch: {
  '$store.state.movies': function() {
    this.movies = this.$store.state.movies
    console.log(this.movies)
  }
  },
  mounted() {
    this.getMovies();
    this.historyWatched();
  },
  methods: {
    async getMovies() {
      axios
        .get(
          "https://api.themoviedb.org/3/movie/popular?api_key=1e448e0dfcdbb565f5d329820065b4d2"
        )
        .then((res) => {
          console.log(res);
          this.movies = res.data.results;  
        });
    },

    imdb(id) {
      axios
        .get(
          `https://api.themoviedb.org/3/movie/${id}?api_key=1e448e0dfcdbb565f5d329820065b4d2`
        )
        .then((res) => {
          window.open("https://www.imdb.com/title/" + res.data.imdb_id);
        });
    },

    watch(idToFind) {
/*       let film = this.movies.find(({ id }) => id === idToFind);
      film.watched = true; */
      this.ids = window.localStorage.getItem("watchedIds") ? JSON.parse(window.localStorage.getItem("watchedIds")) : [];
      console.log('ea',this.ids)
      this.ids.push(idToFind);
      window.localStorage.setItem("watchedIds", JSON.stringify(this.ids));
      this.historyWatched() 
    },

    historyWatched() {
      this.ids = JSON.parse(window.localStorage.getItem("watchedIds"));
    },
  },
};
</script>

<style>
.pagination li {
  margin-top: 20px;
  width: 50px;
  height: 50px;
  margin-right: 5px;
  display: inline-block;
  padding: 0;
}

.pagination li a {
  font-size: 14px;
  font-weight: 400;
  line-height: 50px;
  border-radius: 50%;
  display: block;
  text-decoration: none;
  text-align: center;
  transition: all 0.3s ease;
  color: black;
}

.pagination li a.current-page {
  background: #9352b3;
  color: white;
}

.pagination li a:hover {
  background: rgba(208, 208, 208, 0.6);
  color: #9352b3;
}

.pagination li a.current-page:hover {
  background: #9352b3;
  color: white;
}

.card {
  margin-bottom: 30px;
  background: #343a40;
  border-radius: 5px;
  overflow: hidden;
  min-height: calc(100% - 30px);
  position: relative;
}

.card .card-body {
  text-align: center;
  padding: 20px;
}

.card .card-body .card-title {
  color: white;
  font-weight: 500;
  padding-bottom: 20px;
  font-size: 38px;
}

.card .card-body .card-text {
  color: #948a99;
  font-size: 16px;
  line-height: 24px;
  margin-bottom: 50px;
}

.card .image-content {
  position: relative;
  max-height: 250px;
  overflow: hidden;
}
.card .image-content:after {
  content: "";
  display: block;
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 50%;
  background: linear-gradient(
    to top,
    rgba(52, 58, 64, 1) 0,
    rgba(52, 58, 64, 0) 100%
  );
}

.card .image-content:before {
  content: "";
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #343a40;
  opacity: 0.6;
}

.card .image-content .button {
  position: absolute;
  width: 100%;
  top: 10px;
  left: 0;
  color: white;
}

.card .image-content .button a {
  text-decoration: none !important;
  font-size: 18px;
  opacity: 0.5;
  outline: 0;
  color: white;
}

.card .image-content .button a:hover {
  color: #9352b3;
  opacity: 1;
}

.card .image-content .button .like {
  position: absolute;
  left: 20px;
  top: 0;
}

.card .image-content .button .share {
  position: absolute;
  right: 20px;
  top: 0;
}

.card .image-content .stars {
  position: absolute;
  left: 0;
  bottom: 10px;
  z-index: 10;
  width: 100%;
  text-align: center;
}

.card .image-content .stars .rating i {
  color: #ffc741;
}

.card .image-content .play {
  position: absolute;
  top: 50%;
  left: 50%;
  z-index: 12;
  transform: translate(-50%, -50%);
}

.card .image-content .play .video {
  opacity: 0;
  visibility: hidden;
  transform: scale(0);
  height: 60px;
  width: 60px;
  line-height: 60px;
  color: white;
  border-radius: 50%;
  z-index: 10;
  transition: all 0.5s ease;
  background: #9352b3;
  padding: 25px 30px;
}

.card:hover .image-content .play .video {
  opacity: 1;
  visibility: visible;
}

.card:hover .image-content .button .like,
.card:hover .image-content .button .share {
  color: white;
  opacity: 1;
}

.card .image-content .play .video:hover {
  box-shadow: 0px 0px 0px 13px #9352b3ae;
}

.btn-purple {
  transition: all 0.5s ease;
  font-weight: 600;
  color: white;
  font-size: 14px !important;
  text-transform: uppercase;
  background: #9352b3;
}

.btn-float {
  position: absolute;
  bottom: 20px;
  left: calc(50% - 50px);
}

.btn-purple:hover {
  background: #ad72c9;
  color: white;
}

.body {
  margin: 100px 0;
}

.btn-grey {
  background: #edf5f7;
  color: #999;
  transition: all 0.4s;
}

.btn-grey:hover {
  background: #9352b3;
  color: white;
}

.btn-grey.active {
  background: #9352b3;
  color: white;
}

.filter {
  padding: 10px 20px;
  width: 100%;
  color: #666;
  border: 1px solid #e3e3e3;
  border-radius: 5px;
  height: auto;
  box-shadow: none;
  -moz-appearance: none;
  text-indent: 0.01px;
  text-overflow: "";
  color: black;
  background: white;
  -webkit-appearance: none;
  -ms-appearance: none;
  -o-appearance: none;
  appearance: none;
}

.filter:focus {
  outline: none;
}

.w-select {
  width: 50%;
  float: right;
}

.card .image-content .watched {
  position: absolute;
  left: 0;
  top: 10px;
  z-index: 10;
  width: 100%;
  text-align: center;
}

.watched-text {
  background: #9352b3;
  padding: 5px 10px;
  font-size: 12px;
}
</style>