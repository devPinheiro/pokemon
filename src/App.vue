<template>
    <div class="w-full max-w-screen-xl pt-32  lg:pt-40 mx-auto px-6 sm:pr-20 sm:pl-20  lg:pr-32 lg:pl-32 block mb-4 bg-gray-10 curved">
                  <div class="w-full xl:flex lg:flex ">
                 
                    <div class="block  xl:flex lg:flex text-center lg:text-left text-dark  ">
                        <div class="xl:mt-18 xl:pr-32  lg:mt-18 lg:pr-32 ">
                            <h1 class="font-Montserrat font-bold leading-tight sm:text-3xl md:text-4xl lg:text-5xl xl:text-5xl text-xl ">
                            Pokermon Show
                            </h1>
                            <p class="pt-10"> View all the amazing Pokermon</p>
                        </div>
                    </div>
                    <div class="block xl:flex lg:flex pt-8 m-auto">
                     
                     <!-- Login form -->
                     <Form />
                    
                    </div>
                  </div>
   
  </div>
</template>

<script>
import Form from './components/Form.vue'

export default {
  name: 'app',
  components: {
    Form
  }
}
</script>

<style>
.curved {
    border-radius: 0 0 100% 0;
  }
</style>
