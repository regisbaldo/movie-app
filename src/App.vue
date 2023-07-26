<script setup>
import { ref } from "vue";
import { items } from "./movies.json";
import { StarIcon } from "@heroicons/vue/24/solid";

const movies = ref(items)

</script>

<template>
  <div class="movie-list-container grid grid-cols-3 gap-4 p-5">
    <div class="movie"
      v-for="movie in movies" 
      :key="movie.id"
    >
      <img class="image"
        :src="movie.image"
        :alt="movie.name"
      >

      <div class="info p-5">
        <div class="name-section pb-5">
          <span class="name font-mono font-bold text-xl">{{ movie.name }}</span>

          <div class="genres"
            v-for="(genre, i) in movie.genres"
            :key="i"
          >
            <span class="genre font-semibold text-sm">{{ genre }}</span>
          </div>
        </div>

        <span class="description font-serif"> {{ movie.description }} </span>

        <div class="rating">
          <span class="rating-text font-serif">Rating ({{ movie.rating }}/5)</span>

          <div class="stars">
            <star-icon />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.movie-list-container {
  background-color:#111826;

  & > .movie {
    background: #fcf6f6;

    & > .image {
    }

    & > .info {
      
      & > .name-section {

        & > .name {
          display: block;
          padding-bottom: 5px;
        }

        & > .genres {
          background: #598ceb;
          border-radius: 20px;
          padding: 5px 10px;
          display: inline-block;

          & > .genre {
            color: #fcf6f6;
          }
        }
      }
    }
  }
}
</style>