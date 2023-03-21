<template>
  <div id="arrow-back-container">
    <ArrowBack id="arrow-back" />
  </div>
  <div>
    <template v-for="item in allProducts" :key="item.id">
      <img :src="item.src" alt="" class="product-img" />
    </template>
  </div>
</template>

<script>
  import ArrowBack from '../components/SvgIcons/ArrowBack.vue'
  export default {
    created() {
      this.fetchAllProducts()
    },
    components: {
      ArrowBack
    },
    data() {
      return {
        allProducts: null
      }
    },
    methods: {
      async fetchAllProducts() {
        const response = await fetch('/allProducts.json')
        const result = await response.json()
        this.allProducts = result
        console.log(result)
      }
    }
  }
</script>

<style scoped>
  h1 {
    text-align: center;
    /* margin-top: 1.5em; */
    /* margin-bottom: 1em; */
  }

  div {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1em;
    margin: 0.5em;
    padding-top: 4em;
    justify-items: center;
  }

  img {
    max-width: 100%;
  }

  #arrow-back-container {
    /* width: 100%; */
    top: 50%;
  }
  #arrow-back {
    position: absolute;
  }

  /* KZ tryied to make the images in the same size but also responsive.

   .product-img {
      height: 200px;
    width: 200px;
    object-fit: contain;
  }


  @media screen and (min-width: 576px) {
    .product-img {
      height: auto;
      width: 100%;
    }
  }

  @media screen and (min-width: 992px) {
    .product-img {
      height: auto;
      width: 25%;
    }
  }*/
</style>
