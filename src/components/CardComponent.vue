<template>
  <li>
    Poster:
    <img
      :src="'https://image.tmdb.org/t/p/w342/' + item.poster_path"
      :alt="item.title"
    />
    <br />
    id: {{ item.id }}<br />
    Titolo Originale:
    {{ item.original_title ? item.original_title : item.original_name }}<br />
    Titolo: {{ item.title ? item.title : item.name }}<br />
    Lingua: {{ item.original_language }}

    <img :src="getFlag(item.original_language)" /><br />

    Voto: <i v-html="getStarsRating(item.vote_average)"></i>
    {{ item.vote_average }}<br />
  </li>
</template>

<script>
export default {
  name: "CardComponent",
  props: { item: Object },

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
        default:
          return iso;
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
