<template>
  <div class>
    <div class="block pt-4">
      <button class="w-full ml-auto" @click="logOut">Logout</button>
    </div>
    <section
      class="w-full max-w-screen-xl pt-20 pb-32 lg:pt-40 mx-auto px-6 sm:pr-16 sm:pl-16 lg:pr-16 lg:pl-16 block mb-4"
    >
      <div class="md:flex block">
        <CardGrid :cards="displayCards" />

        <div class="sm:flex block w-1/5 mx-4">
          <h1 class>Filter</h1>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import CardGrid from "@/components/CardGrid.vue";

import axios from "axios";
export default {
  data() {
    return {
      cards: [],
      page: 1,
      perPage: 20,
      url: "https://api.pokemontcg.io/v1/cards",
      pages: []
    };
  },
  components: {
    CardGrid
  },
  methods: {
    // fetches data from API
    fetchCards() {
      axios
        .get(this.url)
        .then(response => {
          this.cards = response.data;
          
        })
        .catch(er => er);
    },
    // populates the number of pages for pagination
    setPages() {
      for (let i = 1; i <= this.perPage; i++) {
        this.pages.push(i);
      }
    },
    // paginate base on the number of cards for each page
    paginateCards() {
      let page = this.page;
      let perPage = this.perPage;
      let from = (page * perPage) - perPage;
      let to = (page * perPage);
      const allCards = this.cards;
      return allCards.slice(from, to);
    },
    // log users out of the app
    logOut() {
      if (localStorage.getItem("pokermonUser")) {
        // if pokermonUser exists clear it from localstorage
        localStorage.removeItem("pokermonUser");
        // redirect to the homepage
        this.$router.push("/");
      }
    }
  },
  computed: {
    displayCards(){
      return this.paginateCards();
    }
  },
  watch: {
    cards(){
      this.setPages();
    }
  },
  // use Vue lifecyle method created, on creating the component fetch the cards
  created(){
    this.fetchCards();
  }
};
</script>

<style scoped>
</style>
