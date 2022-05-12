<template>
  <div class="movie-card">
    <!-- Poster -->
    <div class="poster">
      <img
        v-if="item.poster_path != null"
        :src="'https://image.tmdb.org/t/p/w342/' + item.poster_path"
        :alt="item.title"
      />
      <img
        v-else
        src="https://s.studiobinder.com/wp-content/uploads/2019/06/Movie-Poster-Templates-StudioBinder.jpg"
        width="342px"
        height="488px"
        alt=""
      />
    </div>

    <!-- Infos -->
    <!-- id: {{ item.id }} -->
    <div class="infos">
      <h4>Titolo Originale:</h4>
      <p>
        {{ item.original_title ? item.original_title : item.original_name }}
      </p>
      <h4>Titolo: {{ item.title ? item.title : item.name }}</h4>
      <div>
        <h4>Lingua:</h4>
        <img
          v-if="availableFlags.includes(item.original_language)"
          class="flag"
          :src="getFlag(item.original_language)"
          :alt="`Flag ${item.original_language}`"
        />
        <p v-else class="fw-bold">
          {{ item.original_language }}
        </p>
      </div>

      <h4>Voto:</h4>
      <i class="text-warning" v-html="getStarsRating(item.vote_average)"></i>

      <h4>Overview:</h4>
      {{ item.overview }}
    </div>
  </div>
</template>

<script>
export default {
  name: "CardComponent",
  props: { item: Object },

  data: function () {
    return {
      availableFlags: [
        "it",
        "en",
        "fr",
        "de",
        "es",
        "ru",
        "ko",
        "nl",
        "uk",
        "pt",
        "pl",
        "ja",
        "zh",
      ],
    };
  },

  methods: {
    getStarsRating(rating) {
      let starsRating = Math.ceil(rating / 2);
      let empty = '<i class="fa-regular fa-star"></i>';
      let full = '<i class="fa-solid fa-star"></i>';
      let htmlString = "";
      const emptyStars = 5 - starsRating;
      for (let i = 0; i < starsRating; i++) {
        htmlString += full;
      }
      for (let i = 0; i < emptyStars; i++) {
        htmlString += empty;
      }
      return htmlString;
    },

    getFlag(iso) {
      switch (iso) {
        case "en":
          return "https://flagcdn.com/h40/gb.png";
        case "uk":
          return "https://flagcdn.com/h40/gb.png";
        case "it":
          return "https://flagcdn.com/h40/it.png";
        case "fr":
          return "https://flagcdn.com/h40/fr.png";
        case "es":
          return "https://flagcdn.com/h40/es.png";
        case "de":
          return "https://flagcdn.com/h40/de.png";
        case "ru":
          return "https://flagcdn.com/h40/ru.png";
        case "ko":
          return "https://flagcdn.com/h40/kr.png";
        case "nl":
          return "https://flagcdn.com/h40/nl.png";
        case "pt":
          return "https://flagcdn.com/h40/pt.png";
        case "pl":
          return "https://flagcdn.com/h40/pl.png";
        case "ja":
          return "https://flagcdn.com/h40/jp.png";
        case "zh":
          return "https://flagcdn.com/h40/cn.png";
        default:
          return iso;
      }
    },
  },
};
</script>

<style scoped lang="scss">
.movie-card {
  max-width: 500px;
  max-height: 1000px;
  border: 1px solid black;
  margin: 20px;
  background-color: black;
}
</style>
