<template>
  <div class="common-container">
    <PageHeader></PageHeader>
    <ReservationForm></ReservationForm>
    <div class="coffee-container">
      <div class="coffee-card-container">
        <p class="headline">HotBeverage</p>
        <carousel
          :per-page="3"
          :loop="true"
          :autoplay="true"
          :autoplay-timeout="4000"
          :navigation-enabled="true"
          :paginationEnabled="false"
          class="coffee-card-wrapper"
        >
          <slide> <Card></Card></slide>
          <slide> <Card></Card></slide>
          <slide> <Card></Card></slide>
          <slide> <Card></Card></slide>
          <slide> <Card></Card></slide>
          <slide> <Card></Card></slide>
        </carousel>
        <p class="footline">HotBeverageを全て見る</p>
      </div>
      <div class="coffee-card-container">
        <p class="headline">IceBeverage</p>
        <carousel
          :per-page="3"
          :loop="true"
          :autoplay="true"
          :autoplay-timeout="4000"
          :navigation-enabled="true"
          :paginationEnabled="false"
          class="coffee-card-wrapper"
        >
          <slide> <Card></Card></slide>
          <slide> <Card></Card></slide>
          <slide> <Card></Card></slide>
          <slide> <Card></Card></slide>
          <slide> <Card></Card></slide>
          <slide> <Card></Card></slide>
        </carousel>
        <p class="footline">IceBeverageを全て見る</p>
      </div>
    </div>
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader.vue";
import ReservationForm from "@/components/ReservationForm.vue";
import Card from "@/components/Card.vue";
import Carousel from "vue-carousel/src/Carousel.vue";
import Slide from "vue-carousel/src/Slide.vue";
export default {
  data() {
    return {};
  },
  components: {
    PageHeader,
    ReservationForm,
    Card,
    Carousel,
    Slide,
  },
  async asyncData({ $axios }) {
    const response = await $axios.$get(
      "https://firestore.googleapis.com/v1/projects/otsudori-7fdf5/databases/(default)/documents/posts"
    );
    console.log(response.documents[0].fields);
    console.log(response.documents[1].fields);
    return { posts: response.documents };
  },
};
</script>

<style scoped>
.coffee-container {
  margin-top: 10%;
}
.coffee-block {
  width: 80%;
  margin: 1% auto;
}
.item {
  display: block;
  background-color: #f1f1f1;
}

.coffee-card-wrapper {
  width: 70%;
  margin: 0 auto;
  display: flex;
}
.headline {
  width: 68%;
  margin: 1% auto;
  font-size: 18px;
  font-weight: bold;
}
.footline {
  width: 68%;
  margin: 1% auto;
  font-size: 18px;
  font-weight: bold;
  text-align: right;
}
</style>