<template>
  <div class="block sm:w-4/5">
    <div class="grid lg:h-80">
      <Card v-for="card in cards.cards" :key="card.id">
        <img class="w-full" :src="card.imageUrl" alt="Sunset in the mountains" />
        <div class="px-6 py-4">
          <div class="font-bold text-xl mb-2">{{ card.name }}</div>
        </div>
      </Card>
    </div>

    <div class="flex pt-10">
      <button
        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline mr-auto"
        type="button"
      >Prev</button>

      <button
        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline ml-auto"
        type="button"
      >Next</button>
    </div>
  </div>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
  props: ["cards"],
  components: {
    Card
  }
};
</script>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 1.5rem;
}
@media screen and (min-width: 768px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media screen and (min-width: 992px) {
  .grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media screen and (min-width: 1200px) {
  .grid {
    grid-template-columns: repeat(4, 1fr);
  }
}
</style>