<template>
  <div class="movie-card">
    <!-- Poster -->
    <div class="poster">
      <img
        v-if="item.poster_path !== null"
        :src="'https://image.tmdb.org/t/p/w342/' + item.poster_path"
        :alt="item.title"
      />
      <img
        v-else
        src="https://snipstock.com/assets/cdn/png/69fecd49db5a0817220e9d23299f07f2.png"
        width="342px"
        height="488px"
        alt=""
      />
    </div>

    <!-- Infos -->
    <!-- id: {{ item.id }} -->
    <div class="infos py-3">
      <div class="titles">
        <h4>Titolo Originale:</h4>
        <span>
          {{ item.original_title ? item.original_title : item.original_name }}
        </span>
        <h4 class="pt-3">Titolo:</h4>
        <span>{{ item.title ? item.title : item.name }}</span>
      </div>
      <div class="year">
        <h4>Data di rilascio:</h4>
        <span v-if="item.release_date !== null && item.release_date !== ''">{{
          item.release_date
        }}</span>
        <span v-else>N/A</span>
      </div>

      <div class="language py-2">
        <h4>Lingua:</h4>
        <img
          v-if="availableFlags.includes(item.original_language)"
          class="flag"
          :src="getFlag(item.original_language)"
          :alt="`Flag ${item.original_language}`"
        />
        <div v-else class="lang-placeholder">
          <p class="fw-bold">{{ item.original_language }}</p>
        </div>
      </div>

      <div class="votes py-2">
        <h4>Voto:</h4>
        <span
          ><i
            class="text-warning"
            v-html="getStarsRating(item.vote_average)"
          ></i
        ></span>
      </div>
      <div class="overview">
        <h4>Overview:</h4>
        <p>{{ item.overview }}</p>
      </div>
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
  width: 342px;
  padding: 0;
  height: auto;
  border: 1px solid white;
  margin: 20px;
  background-color: black;
  overflow: hidden;
  position: relative;
  cursor: pointer;

  .poster {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .infos {
    display: flex;
    flex-flow: column;
    background-color: #111111;
    width: 100%;
    height: 100%;
    padding: 20px;
    visibility: hidden;
    position: absolute;
    color: white;
    top: 0;
    left: 0;
    z-index: 2;
  }

  h4 {
    font-weight: bold;
  }

  .titles {
    padding-bottom: 10px;
    span {
      font-size: 20px;
    }
  }

  .votes,
  .language {
    display: flex;
    align-items: center;
    gap: 25px;
  }
}

.movie-card:hover .infos {
  visibility: visible;
  overflow-y: scroll;
}

.lang-placeholder {
  height: 40px;
  width: 70px;
  border: 1px solid white;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: 13px;
  background-color: blue;
  p {
    font-weight: bold;
    font-size: 20px;
    text-transform: uppercase;
  }
}
</style>
