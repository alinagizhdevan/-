<template>
  <div class="product">
    <div class="row product__controls">
      <div class="col-sm-12 col-md-6 col-lg-4 col-xl-3">

        <select v-model="productType" class="product_types" @change="sendProductType">
          <option disabled class="product_type product_type_disabled" value="">Choose operation type:</option>
          <option class="product_type product_type_active" value="tenRarestWords">10 rarest words</option>
          <option class="product_type product_type_active" value="tenMostCommonWords">10 most common words</option>
          <option disabled class="product_type product_type_disabled" value="type3">Type3</option>
        </select>

      </div>


    </div>
  </div>
</template>

<script>
export default {
  name: "ProductsTypeDropdown.vue",
  data: () => ({
    productType: '',
  }),
  methods: {
    sendProductType() {
      this.$emit('sendType', this.productType)
    }
  },
}
</script>

<style lang="scss" scoped>

.product {
  display: flex;
  flex-direction: column;

  &__controls {
    margin: 20px 0;
  }

  &_types {
    margin-top: 10px;
    padding: 0.5em 1.5em;
    width: calc(100% + 5px); // add 5 as border
    font-size: 1.2em;
    background-color: #008CBA;
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-right: 5px solid #008CBA;
    border-radius: 5px;

    &:hover {
      background-color: white;
      color: black;
      border-right: 5px solid white;
    }
  }

  &_type {
    font-size: 1em;
    display: block;
    padding: 0.5rem 1.5rem;

    &_active {
      background-color: white;
      color: black;

      &:hover {
        background-color: #00a9e2;
        color: #fff;
      }
    }

    &_disabled {
      background-color: #cccccc;
    }
  }
}

</style>


<!--      <div class="col-sm-12 col-md-6 col-lg-4 col-xl-3 dropdown">-->
<!--        <a class="btn dropdown-toggle product_types" href="#" role="button" id="dropdownMenuLink"-->
<!--           data-toggle="dropdown" aria-haspopup="true" aria-expanded="true">-->
<!--          Choose product type:-->
<!--        </a>-->
<!--        &lt;!&ndash;          @click="showHideDropdown"&ndash;&gt;-->

<!--&lt;!&ndash;        v-if="dropdownIsOpen"&ndash;&gt;-->
<!--        <div class="dropdown-menu dropdown-menu-left dropdown-menu-lg-right" aria-labelledby="dropdownMenuLink"-->
<!--             data-bar-is="close" >-->
<!--          <div class="dropdown-header">Choose product type</div>-->
<!--          &lt;!&ndash;                    <a class="dropdown-item product_type disabled" href="#">10 most common words</a>&ndash;&gt;-->
<!--          &lt;!&ndash;                    <div class="dropdown-divider"></div>&ndash;&gt;-->
<!--          <a class="dropdown-item product_type" href="#" data-type="ten-rarest-words">10 rarest words</a>-->
<!--          <div class="dropdown-divider"></div>-->
<!--          <a class="dropdown-item product_type active" href="#" data-type="ten-most-common-words">10 most common-->
<!--            words</a>-->
<!--          <div class="dropdown-divider"></div>-->
<!--          <a class="dropdown-item product_type disabled" href="#" data-type="type4">Type4</a>-->
<!--          <div class="dropdown-divider"></div>-->
<!--          <a class="dropdown-item product_type disabled" href="#" data-type="type5">Type5</a>-->
<!--          <div class="dropdown-divider"></div>-->
<!--          <a class="dropdown-item product_type disabled" href="#" data-type="type6">Type6</a>-->
<!--          <div class="dropdown-divider"></div>-->
<!--          <a class="dropdown-item product_type disabled" href="#" data-type="type7">Type7</a>-->
<!--        </div>-->
<!--      </div>-->

<!--    </div>-->
