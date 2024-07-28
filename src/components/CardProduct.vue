<template>
  <div :class="['card-product', { 'card-product-large': isLarge }]">
    <div class="image-container">
      <img
        :src="imageSrc"
        alt="Product"
        :class="['product-img', { 'product-img-large': isLarge }]"
        :style="{ opacity: isOpacity ? '0.3' : '0.5' }"
      />

      <div class="badge-container">
        <span class="badge-text">Хит продаж</span>
        <img src="/icons.png" alt="Icons" class="icons" />
      </div>

      <div class="discount">
        <span>25%</span>
      </div>
    </div>

    <div class="description-container">
      <div class="brand">Брэнд</div>
      <div class="product-name">
        Полное название товара в несколько строк для вида с обрывом в конце...
      </div>
    </div>

    <div class="price-container">
      <span class="current-price">5 990 ₽</span>
      <span class="original-price">5 990 ₽</span>
    </div>

    <button :class="['buy-button', { 'buy-button-opacity': isOpacity }]">
      {{ isOpacity ? "Сообщить о поступлении" : "Купить" }}
    </button>
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  props: {
    isLarge: {
      type: Boolean,
      default: false,
    },
    imageSrc: {
      type: String,
      default: "/product-img.png",
    },
    isOpacity: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" scoped>
.card-product {
  max-width: 333px;
  height: 356px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
  border-radius: 4px;

  @media (max-width: 1440px) {
    width: 213px;
    height: 372px;
    gap: 16px;
    border-radius: 4px;
  }
  @media (max-width: 375px) {
    width: 165.5px;
    height: 360px;
    gap: 12px;
    border-radius: 4px;
  }

  .image-container {
    width: 100%;
    height: 200px;
    background: #f8f8fa;
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    gap: 0px;
    @media (max-width: 1440px) {
      width: 100%;
      height: 200px;
      gap: 0px;
    }

    .product-img {
      width: 60px;
      height: 60px;
      position: absolute;
      top: 50%;
      left: 50%;
      padding: 0.07px 0px;
      opacity: 0.5;
      transform: translate(-50%, -50%);
      @media (max-width: 1440px) {
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
      }
    }
    .product-img-large {
      width: 82px;
      height: 82px;
      top: 50%;
      left: 50%;
      padding: 0.1px 0px;
      opacity: 0.5;
      transform: translate(-50%, -50%);
      @media (max-width: 1440px) {
        width: 82px;
        height: 82px;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
      }
    }

    .badge-container {
      max-width: 112px;
      height: 32px;
      position: absolute;
      top: 12px;
      left: 12px;
      display: flex;
      align-items: center;
      gap: 4px;

      .icons {
        width: 20px;
        height: 20px;
        padding: 2.5px 3.33px;
      }

      .badge-text {
        width: 72px;
        height: 16px;
        font-family: PT Sans;
        font-size: 14px;
        font-weight: 400;
        line-height: 16px;
        text-align: right;
        color: $color-font-main;
      }
    }

    .discount {
      width: 48px;
      height: 26px;
      position: absolute;
      top: 162px;
      left: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      background-color: $color-brand;
      border-radius: 4px;
      padding: 6px 10px;

      span {
        width: 28px;
        height: 14px;
        font-family: PT Sans;
        font-size: 14px;
        font-weight: 700;
        line-height: 14px;
        text-align: right;
        color: #ffffff;
      }
    }
  }

  .description-container {
    width: 100%;
    height: 56px;
    display: flex;
    flex-direction: column;
    gap: 8px;
    @media (max-width: 1440px) {
      width: 100%;
      height: 72px;
      gap: 8px;
    }

    .brand {
      width: 100%;
      height: 16px;
      font-family: PT Sans;
      font-size: 14px;
      font-weight: 400;
      line-height: 16px;
      text-align: left;
      color: $color-font-second;
    }

    .product-name {
      width: 100%;
      height: 32px;
      font-family: PT Sans;
      font-size: 14px;
      font-weight: 400;
      line-height: 16px;
      text-align: left;
      color: $color-font-main;
      overflow: hidden;
      text-overflow: ellipsis;
      display: -webkit-box;
      line-clamp: 2;
      -webkit-box-orient: vertical;
      @media (max-width: 1440px) {
        width: 100%;
        height: 48px;
        gap: 0px;
      }
    }
  }

  .price-container {
    width: 100%;
    height: 14px;
    display: flex;
    gap: 8px;

    .current-price {
      width: 54px;
      height: 14px;
      font-family: PT Sans;
      font-size: 16px;
      font-weight: 700;
      line-height: 14px;
      text-align: left;
      color: $color-font-main;
    }

    .original-price {
      width: 40px;
      height: 14px;
      font-family: PT Sans;
      font-size: 12px;
      font-weight: 400;
      line-height: 14px;
      text-align: left;
      color: $color-font-second;
      text-decoration: line-through;
    }
  }

  .buy-button {
    width: 75px;
    height: 38px;
    padding: 12px 16px;
    gap: 4px;
    border-radius: 4px;
    border: 1px solid $color-brand;
    background-color: white;
    display: flex;
    align-items: center;
    justify-content: start;
    cursor: pointer;
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 700;
    line-height: 14px;
    color: $color-brand;
    margin-top: auto;
    align-self: flex-start;
    transition: background-color 0.3s ease, color 0.3s ease;
    &:hover {
      background-color: $color-brand;
      color: white;
    }
  }
  .buy-button-opacity {
    width: 100%;
    height: 38px;
    padding: 12px, 16px, 12px, 16px;
    gap: 4px;
    border-radius: 4px;
    border: 1px solid $color-font-second;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 700;
    line-height: 14px;
    color: $color-font-second;
    transition: background-color 0.3s ease, color 0.3s ease;
    &:hover {
      background-color: $color-brand;
      color: white;
    }
  }
}
</style>
