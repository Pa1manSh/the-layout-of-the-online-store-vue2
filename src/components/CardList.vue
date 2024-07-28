<template>
  <div>
    <div class="card-list">
      <div class="row-card">
        <CardProduct />
        <CardProduct :isLarge="true" imageSrc="/product-img-large.png" />
        <CardProduct :isOpacity="true" imageSrc="/product-img.png" />
        <CardProduct />
      </div>
      <div class="row-card">
        <CardProduct />
        <CardProduct />
        <CardProduct />
        <CardProduct />
      </div>
      <div class="row-card">
        <CardProduct />
        <CardProduct />
        <CardProduct />
        <CardProduct />
      </div>
    </div>

    <div class="card-list-mobile">
      <div class="row-card-mobile">
        <CardProduct />
        <CardProduct />
      </div>
      <div class="row-card-mobile">
        <CardProduct />
        <CardProduct />
      </div>
      <div class="row-card-mobile">
        <CardProduct />
        <CardProduct />
      </div>
    </div>
  </div>
</template>

<script>
import CardProduct from "./CardProduct.vue";

export default {
  name: "CardList",
  components: {
    CardProduct,
  },
};
</script>

<style scoped>
.card-list {
  width: 1404px;
  height: 1132px;
  display: flex;
  flex-wrap: wrap;
  gap: 24px;

  @media (max-width: 1440px) {
    width: 924px;
    height: 1164px;
    gap: 24px;
  }
  @media (max-width: 375px) {
    display: none;
  }
}
.row-card {
  width: 100%;
  height: 372px;
  display: flex;
  gap: 24px;

  @media (max-width: 1440px) {
    width: 100%;
    height: 372px;
    gap: 24px;
  }
}
@media (max-width: 1225px) {
  .row-card {
    width: 343px;
    height: auto;
    flex-wrap: wrap;
  }

  /* .card-product {
    width: calc(33.33% - 16px);
  } */
}

.card-list-mobile {
  max-width: 375px;
  height: 1112px;
  padding: 0 16px;
  gap: 16px;
  display: flex;
  flex-wrap: wrap;

  @media (min-width: 376px) {
    display: none;
  }
}
.card-list-mobile {
  max-width: 375px;
  height: 1112px;
  padding: 0 16px;
  gap: 16px;
  display: none;
  display: flex;

  @media (max-width: 375px) {
    display: flex;
    flex-wrap: wrap;
  }
}

.row-card-mobile {
  max-width: 343px;
  height: 360px;
  display: flex;
  gap: 12px;
}
</style>
