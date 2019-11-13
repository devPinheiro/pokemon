<template>
    <div class="w-full max-w-screen-xl pt-32  lg:pt-40 mx-auto px-6 sm:pr-20 sm:pl-20  lg:pr-32 lg:pl-32 block mb-4 bg-gray-10 ">
                  <div class="w-full xl:flex lg:flex ">
                 
                    <div class="block  xl:flex lg:flex text-center lg:text-left text-dark  ">
                        <div class="xl:mt-18 xl:pr-32  lg:mt-18 lg:pr-32 ">
                          <h2 class="font-Montserrat font-thin  sm:text-lg md:text-xl lg:text-5xl pt-4 pb-2 text-dark-400 xl:pr-16 ">
                            Hi, I'm <span class="font-medium">Samuel</span>
                            </h2>
                            <h1 class="font-Montserrat font-bold leading-tight sm:text-3xl md:text-4xl lg:text-5xl xl:text-5xl text-xl ">
                            Developer & Designer
                            </h1>

                            <p class="pt-10">I enjoy building digital products  with great user experience.  I’m currently available
to build your next big thing.</p>
                        </div>
                    </div>
                    <div class="block xl:flex lg:flex text-center lg:text-left hidden lg:show pt-8 m-auto  ">
                     
                     <!--  -->
                    </div>
                  </div>
   
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
