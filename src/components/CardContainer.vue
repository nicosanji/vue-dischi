<template>
  <div class="container">
    <div class="row">
      <Select :genreList="genreList" @selectClick="onSelectGenre"></Select>
    </div>
    <div class="row row-cols-5 gy-5">
      <Card
        v-for="(cd, i) in listByGenre"
        :key="i"
        :author="cd.author"
        :title="cd.title"
        :year="cd.year"
        :poster="cd.poster"
        :genre="cd.genre"
      ></Card>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./Card.vue";
import Select from "./Select.vue";

export default {
  components: { Card, Select },
  name: "CardContainer",
  data() {
    return {
      cdList: [],
      selectedGenre: "",
    };
  },
  // methods -> modifico i dati
  methods: {
    onSelectGenre(selection) {
      this.selectedGenre = selection;
    },
  },
  // computed -> modifico il modo in cui vengono visualizzati i dati
  computed: {
    genreList() {
      const genreObject = {};
      this.cdList.forEach((cd) => {
        const { genre } = cd;
        if (!genreObject[genre]) {
          genreObject[genre] = 0;
        }
        genreObject[genre]++;
      });
      return genreObject;
    },
    listByGenre() {
      if (!this.selectedGenre) {
        return this.cdList;
      }
      return this.cdList.filter((cd) => {
        return this.selectedGenre === cd.genre;
      });
    },
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.cdList = resp.data.response;
      });
  },
};
</script>
