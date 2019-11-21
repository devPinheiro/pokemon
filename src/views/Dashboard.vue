<template>
  <div class>
    <div class="flex pt-4 ">
      <button class="w-full ml-auto" @click="logOut">Logout</button>
    </div>
    <section
      class="w-full max-w-screen-xl pt-20 pb-32 lg:pt-40 mx-auto px-6 sm:pr-16 sm:pl-16 lg:pr-16 lg:pl-16 block mb-4"
    >
      <div class="md:flex block">

        <div class="sm:flex block w-1/5 mx-4">
        <div class="block">
         <h1 class>Filter</h1>
          <app-filter :filterItem="items" v-on:check-filter="checkFilter"></app-filter>
        </div>
        </div>
          
        <app-card-grid :cards="cards" :rarityProp="Rarity" :setProp="Sets" :typeProp="Type"></app-card-grid>
        
      </div>
    </section>
  </div>
</template>

<script>
import CardGrid from "@/components/CardGrid.vue";
import Filter from "@/components/Filter.vue";

import axios from "axios";
export default {
  data() {
    return {
      cards: [],
      Rarity: [],
      Type: [],
      Sets: [],
      items: [
        {
        Set: ["Legends Awakened", "Crystal Guardians", "POP Series 9", "Ancient Origins", "Deoxys", "Detective Pikachu", "Kalos Starter Set" ]
      },
       {
        Rarity: ['Common', 'Uncommon', 'Rare']
      }, 
      {
        Types: ['Grass', 'Fire', 'Darkness', 'Colorless', 'Fairy', 'Fighting', 'Metal', 'Water', 'Psychic','Lightning']
        }
      ],
      url: "https://api.pokemontcg.io/v1/cards"
    };
  },
  components: {
    "app-card-grid":CardGrid,
    "app-filter":Filter
  },
  methods: {
    // fetches data from API
    fetchCards() {
      axios
        .get(this.url)
        .then(response => {
          const { cards } = response.data;
          this.cards =  cards
        })
        .catch(er => er);
    },
    // log users out of the app
    logOut() {
      if (localStorage.getItem("pokermonUser")) {
        // if pokermonUser exists clear it from localstorage
        localStorage.removeItem("pokermonUser");
        // redirect to the homepage
        this.$router.push("/");
      }
    },
     // listens for emitted event from the app-filter-checkbox and populate filterItem array
  checkFilter(category, title, checked){
    if(checked){
      
      this[category].push(title);
    } else {
      let index = this[category].indexOf(title);
      if(index > -1){
        this[category].splice(index, 1);
      }
    }
  },

   
  },
 
  // use Vue lifecyle method created, on creating the component fetch the cards
  created(){
    this.fetchCards();
  }

 
};
</script>

<style scoped>
</style>
