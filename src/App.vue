<template>
  <div class="container mx-auto">
    <h2 class="text-3xl font-bold mb-4 mx-3">
        Stocks App
    </h2>
    <Stocks/>
  </div>
</template>

<script>
  import Stocks from './components/Stocks.vue'
  export default{
      components:{
        Stocks
      }
  }
</script>
