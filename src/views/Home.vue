<template>
  <div
    class="w-full max-w-screen-xl pt-20 pb-32 lg:pt-40 mx-auto px-6 sm:pr-20 sm:pl-20 lg:pr-32 lg:pl-32 block mb-4 bg-blue curve"
  >
    <div class="w-full xl:flex lg:flex">
      <div class="block xl:flex lg:flex text-center lg:text-left text-dark">
        <div class="xl:mt-18 xl:pr-32 lg:mt-18 lg:pr-32">
          <h1
            class="font-Montserrat text-white font-bold leading-tight sm:text-3xl md:text-4xl lg:text-5xl xl:text-5xl text-xl"
          >Pokermon Show</h1>
          <p class="pt-10 text-white">View all the amazing Pokermon</p>
        </div>
      </div>
      <div class="block xl:flex lg:flex pt-8 w-1/2 m-auto">
        <!-- Login form -->
        <LoginForm />
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import LoginForm from "@/components/LoginForm.vue";

export default {
  name: "home",
  components: {
    LoginForm
  }
};
</script>


<style scoped>
.curve {
  border-radius: 0 0 90% 0;
}
.bg-blue {
  background: linear-gradient(
    90deg,
    rgba(18, 35, 232, 1) 0%,
    rgb(62, 185, 209) 82%
  );
}
</style>
