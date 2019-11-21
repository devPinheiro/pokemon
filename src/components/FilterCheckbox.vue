<template>
  <div>
   <input class="mr-2 mt-1" type="checkbox" @click="checkFilter"/>
        <span class="text-sm">{{ item }}</span>
  </div>
</template>

<script>
  export default {
    props: ['item', 'category'],
    methods: {
      checkFilter(){
       this.checked = !this.checked
       this.$emit('check-filter', this.category, this.item, this.checked)
    }
    }
  }
</script>

<style scoped>

</style>