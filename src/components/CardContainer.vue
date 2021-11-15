<template>
  <div class="container">
    <div class="row row-cols-5">
      <Card
        v-for="(cd, i) in cdList"
        :key="i"
        :author="cd.author"
        :title="cd.title"
        :year="cd.year"
        :poster="cd.poster"
      ></Card>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./Card.vue";

export default {
  components: { Card },
  name: "CardContainer",
  data() {
    return {
      cdList: [],
    };
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
