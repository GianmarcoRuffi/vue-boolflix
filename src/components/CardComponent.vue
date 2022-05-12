<template>
  <div class="movie-card">
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

    <!-- id: {{ item.id }} -->
    Titolo Originale:
    {{ item.original_title ? item.original_title : item.original_name }}<br />
    Titolo: {{ item.title ? item.title : item.name }}<br />
    Lingua:
    <img
      v-if="availableFlags.includes(item.original_language)"
      class="flag"
      :src="getFlag(item.original_language)"
      :alt="`Flag ${item.original_language}`"
    />
    <p v-else class="fw-bold">
      {{ item.original_language }}
    </p>
    <br />

    Voto: <i v-html="getStarsRating(item.vote_average)"></i>

    Overview: {{ item.overview }}
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
}
</style>
