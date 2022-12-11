<template>
  <div id="app">
    <main class="main">
      <!--    <Header />-->
      <ProductsTypeDropdown
          @sendType="fetchProductType"
      />
      <butFind
          :product-type="this.type"
          :input-data="this.inpData"
          @sendResult="fetchResult"
      />
      <Inputs
          @sendInput="fetchInput"
          @clearResult="fetchEmptyResult"
          :result-text="this.resData"
      />
      <Footer/>
    </main>


  </div>
</template>

<script>
// import Header from "@/components/header/Header";
import ProductsTypeDropdown from "@/components/product/ProductsTypeDropdown";
import butFind from "@/components/product/butFind";
import Inputs from "@/components/input/Inputs";
import Footer from "@/components/footer/Footer";

export default {
  name: 'App',
  data: () => ({
    type: '',
    inpData: '',
    resData: '',
  }),
  components: {
    // Header,
    ProductsTypeDropdown,
    butFind,
    Inputs,
    Footer
  },
  methods: {
    fetchProductType(type) {
      this.type = type;
      this.fetchEmptyResult();
    },

    fetchInput(text) {
      this.inpData = text;
    },

    fetchResult(text) {
      this.resData = text;
    },

    fetchEmptyResult() {
      this.resData = '';
    },

  },

}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;

  background-color: #000;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.main {
  width: 95%;
  padding: 10px;
  display: flex;
  flex-direction: column;
}

</style>
