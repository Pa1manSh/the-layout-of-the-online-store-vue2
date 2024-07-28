<template>
  <div class="filter-container">
    <div class="categories">
      <ul class="category-list">
        <li class="category-label first">
          <span class="name">Название категории</span>
          <span class="count">3</span>
        </li>
        <li class="category-label">
          <span class="name">Название категории</span>
          <span class="count">3</span>
        </li>
        <li class="category-label">
          <span class="name">Название категории</span>
          <span class="count">3</span>
        </li>
        <li class="category-label">
          <span class="name">Название категории</span>
          <span class="count">3</span>
        </li>
      </ul>
    </div>
    <div class="slide-filter">
      <div class="slide-filter-header">
        <span class="price-label">Цена</span>
      </div>
      <div class="price-filter">
        <div class="price-input start">
          <span class="label">от</span>
          <input type="text" class="value" placeholder="0" />
        </div>
        <div class="separator"></div>
        <div class="price-input end">
          <span class="label">до</span>
          <input type="text" class="value" placeholder="10000" />
        </div>
      </div>
    </div>
    <div class="checkbox-filter">
      <div class="brand-filter">
        <span class="brand-label">Брэнд</span>
        <button class="clear-button">Очистить</button>
      </div>
      <div class="brand-search">
        <div class="brand-input">
          <img src="/search-img.png" class="search-img" />
          <input
            v-model="searchText"
            @input="updateClearButtonVisibility"
            type="text"
            class="search-placeholder"
            placeholder="Поиск"
          />
          <div class="clear-button1" v-if="searchText" @click="clearSearch">
            <img src="/text-del2.png" alt="Clear" />
          </div>
        </div>
        <div v-if="searchText" class="search-result">
          По вашему запросу ничего не найдено
        </div>
      </div>

      <div class="attribute-container">
        <div
          v-for="(attribute, index) in attributes"
          :key="index"
          class="attribute-label"
        >
          <div class="checkbox-text">
            <input
              type="checkbox"
              v-model="attributes[index].active"
              :id="'checkbox-' + index"
              class="checkbox"
            />
            <label :for="'checkbox-' + index" class="attribute-name"
              >Атрибут</label
            >
          </div>
          <span class="count">3</span>
        </div>
      </div>

      <div class="size-filter">
        <div class="size-text">Размер</div>

        <div class="size-attribute-container">
          <div
            v-for="(attribute, index) in attributes"
            :key="index"
            class="attribute-label"
          >
            <div class="checkbox-text">
              <input
                type="checkbox"
                v-model="attributes[index].active"
                :id="'checkbox-' + index"
                class="checkbox"
              />
              <label :for="'checkbox-' + index" class="attribute-name"
                >Атрибут</label
              >
            </div>
            <span class="count">3</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import checkmark from "@/assets/checkmark.svg";
export default {
  name: "AppFilter",
  data() {
    return {
      attributes: [
        { active: false },
        { active: false },
        { active: false },
        { active: false },
        { active: false },
        { active: false },
      ],
      checkmark,
      searchText: "",
    };
  },
  methods: {
    clearSearch() {
      this.searchText = "";
    },
    updateClearButtonVisibility() {},
  },
};
</script>

<style lang="scss" scoped>
.filter-container {
  width: 280px;
  height: 760px;
  gap: 28px;

  overflow: hidden;
  @media (max-width: 375px) {
    display: none;
  }

  .categories {
    width: 100%;
    height: 120px;
    gap: 0px;
  }

  .category-list {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }

  .category-label {
    width: 100%;
    height: 30px;
    display: flex;
    align-items: center;
    padding: 0px 16px 0px 32px;
    gap: 0px;
    justify-content: space-between;
    transition: color 0.2s, background-color 0.2s;
    white-space: nowrap;
    box-sizing: border-box;
  }

  .category-label.first {
    padding: 0px 16px 0px 8px;
  }

  .name {
    width: 124px;
    height: 16px;
    font-family: PT Sans, sans-serif;
    font-size: 14px;
    font-weight: 400;
    line-height: 16px;
    text-align: left;
    color: $color-font-main;
    flex: 1;
  }

  .count {
    width: 7px;
    height: 14px;
    font-family: PT Sans, sans-serif;
    font-size: 12px;
    font-weight: 400;
    line-height: 14px;
    text-align: right;
    color: $color-font-second;
  }

  .category-label:hover .name {
    color: $color-white;
  }

  .category-label:active .name {
    background-color: $color-font-bg;
    color: $color-font-main;
    border-radius: 3px;
  }
  .slide-filter {
    width: 100%;
    height: 72px;
    gap: 16px;
    display: flex;
    flex-direction: column;
    background-color: #f9f9f9;
    padding: 16px 0;
  }

  .slide-filter-header {
    width: 100%;
    height: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .price-label {
    width: 36px;
    height: 20px;
    font-family: PT Sans, sans-serif;
    font-size: 16px;
    font-weight: 700;
    line-height: 20px;
    text-align: center;
    color: $color-font-main;
  }
  .price-filter {
    width: 100%;
    height: 36px;
    gap: 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .price-input {
    width: 100%;
    height: 36px;
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .price-input.start {
    box-sizing: border-box;
    width: 119px;
    height: 36px;
    border-radius: 4px;
    border: 1px solid $color-border;
    padding: 10px 8px 10px 8px;
    gap: 6px;
    &:hover {
      border-color: #73aff4;
    }
  }

  .price-input.end {
    box-sizing: border-box;
    height: 36px;
    width: 119px;
    border-radius: 4px;
    border: 1px solid $color-border;
    padding: 10px 8px 10px 8px;
    gap: 6px;
    &:hover {
      border-color: #73aff4;
    }
  }

  .label {
    font-family: PT Sans, sans-serif;
    font-size: 12px;
    font-weight: 400;
    line-height: 14px;
    text-align: left;
    color: $color-font-second;
  }

  .value {
    width: 46px;
    height: 16px;
    font-family: PT Sans, sans-serif;
    font-size: 14px;
    font-weight: 400;
    line-height: 16px;
    text-align: left;
    color: $color-font-main;
    border: none;
    outline: none;
  }

  .separator {
    width: 10px;
    height: 1px;
    background-color: $color-border;
  }
  .checkbox-filter {
    width: 100%;
    height: 268px;
    gap: 16px;

    .brand-filter {
      width: 100%;
      height: 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-top: 10px;
      margin-bottom: 10px;

      .brand-label {
        width: 44px;
        height: 20px;
        font-family: PT Sans, sans-serif;
        font-size: 16px;
        font-weight: 700;
        line-height: 20px;
        text-align: left;
        color: $color-font-main;
      }

      .clear-button {
        width: 48px;
        height: 13px;
        display: flex;
        align-items: center;
        justify-content: flex-end;
        background: none;
        border: none;
        cursor: pointer;

        font-family: PT Sans, sans-serif;
        font-size: 12px;
        font-weight: 400;
        line-height: 12px;
        text-align: right;
        color: $color-font-second;
        text-decoration: underline;
      }
    }
    .brand-search {
      box-sizing: border-box;
      margin-top: 10px;
      width: 280px;
      height: 36px;
      padding: 10px 12px 10px 12px;
      gap: 8px;
      border-radius: 4px;
      border: 1px solid $color-border;
      display: flex;
      align-items: center;
      position: relative;
      flex-direction: column;
      &:hover {
        border-color: #73aff4;
      }

      .brand-input {
        width: 256px;
        height: 16px;
        gap: 8px;
        display: flex;
        align-items: center;
        position: relative;

        .search-img {
          width: 16px;
          height: 16px;
          opacity: 0.3;
        }

        .search-placeholder {
          width: calc(100% - 20px);
          width: 100%;
          height: 16px;
          font-family: PT Sans, sans-serif;
          font-size: 14px;
          font-weight: 400;
          line-height: 16px;
          text-align: left;
          color: $color-font-second;
          border: none;
          outline: none;
          background: none;
          padding: 0;
        }
        .clear-button1 {
          width: 16px;
          height: 16px;
          position: absolute;
          right: 0px;
          display: flex;
          align-items: center;
          justify-content: center;
          opacity: 0;
          transition: opacity 0.2s ease;
          box-sizing: border-box;

          img {
            width: 13.33px;
            height: 13.33px;
          }
        }
      }
      .brand-input input:not(:placeholder-shown) ~ .clear-button1 {
        opacity: 0.3;
      }
      .search-result {
        width: 280px;
        height: 16px;
        margin-top: 10px;
        margin-bottom: 10px;
        box-sizing: border-box;
        white-space: nowrap;
        color: $color-font-main;
        font-family: PT Sans, sans-serif;
        font-size: 14px;
        font-weight: 400;
        line-height: 16px;
        text-align: justify;
      }
    }
    .attribute-container {
      margin-top: 25px;
      width: 100%;
      height: 180px;
      gap: 12px;
      display: flex;
      flex-direction: column;

      .attribute-label {
        width: 100%;
        height: 20px;
        display: flex;
        align-items: center;
        padding: 0px 16px 0px 0px;
        gap: 0px;
        justify-content: space-between;
        white-space: nowrap;
        box-sizing: border-box;

        .checkbox-text {
          width: 81px;
          height: 20px;
          display: flex;
          align-items: center;
          gap: 12px;
          position: relative;

          .checkbox {
            display: none;
          }

          .checkbox + .attribute-name::before {
            content: "";
            display: inline-block;
            width: 20px;
            height: 20px;
            border-radius: 3px;
            border: 1px solid $color-border;
            background-color: #ffffff;
            cursor: pointer;
            margin-right: 10px;
            position: relative;
            vertical-align: middle;
          }
          .checkbox + .attribute-name::after {
            content: "";
            position: absolute;
            width: 10.19px;
            height: 8.11px;
            top: 7px;
            left: 6px;
            display: none;
            background-image: url(~@/assets/checkmark.svg);
            background-size: cover;
          }

          .checkbox:checked + .attribute-name::before {
            background-color: $color-white;
            border: 1px solid $color-white;
          }
          .checkbox:checked + .attribute-name::after {
            display: inline-block;
          }
          .checkbox + .attribute-name:hover::before {
            border-color: $color-white;
          }

          .attribute-name {
            width: 49px;
            height: 16px;
            font-family: PT Sans, sans-serif;
            font-size: 14px;
            font-weight: 400;
            line-height: 16px;
            text-align: left;
            color: $color-font-main;
            cursor: pointer;
            display: inline-block;
          }
        }

        .count {
          width: 7px;
          height: 14px;
          font-family: PT Sans, sans-serif;
          font-size: 12px;
          font-weight: 400;
          line-height: 14px;
          text-align: right;
          color: $color-font-second;
        }
      }
    }
    .size-filter {
      width: 100%;
      height: 216px;
      gap: 16px;
      display: flex;
      flex-direction: column;
      margin-top: 25px;

      .size-text {
        width: 100%;
        height: 20px;
        display: flex;
        align-items: center;
        justify-content: center;
        color: $color-font-main;
        font-family: PT Sans, sans-serif;
        font-size: 16px;
        font-weight: 700;
        line-height: 20px;
        text-align: left;
      }

      .size-attribute-container {
        width: 100%;
        height: 180px;
        gap: 12px;
        display: flex;
        flex-direction: column;

        .attribute-label {
          width: 100%;
          height: 20px;
          display: flex;
          align-items: center;
          padding: 0 16px 0 0;
          gap: 0;
          justify-content: space-between;
          white-space: nowrap;
          box-sizing: border-box;

          .checkbox-text {
            width: 81px;
            height: 20px;
            display: flex;
            align-items: center;
            gap: 12px;
            position: relative;

            .checkbox {
              display: none;
            }

            .checkbox + .attribute-name::before {
              content: "";
              display: inline-block;
              position: relative;
              width: 20px;
              height: 20px;
              border-radius: 3px;
              border: 1px solid $color-border;
              background-color: #ffffff;
              cursor: pointer;
              margin-right: 10px;
              vertical-align: middle;
            }

            .checkbox + .attribute-name::after {
              content: "";
              position: absolute;
              width: 10.19px;
              height: 8.11px;
              top: 7px;
              left: 6px;
              display: none;
              background-image: url(~@/assets/checkmark.svg);
              background-size: cover;
            }

            .checkbox:checked + .attribute-name::before {
              background-color: $color-white;
              border: 1px solid $color-white;
            }

            .checkbox:checked + .attribute-name::after {
              display: inline-block;
            }
            .checkbox + .attribute-name:hover::before {
              border-color: $color-white;
            }

            .attribute-name {
              width: 49px;
              height: 16px;
              font-family: PT Sans, sans-serif;
              font-size: 14px;
              font-weight: 400;
              line-height: 16px;
              text-align: left;
              color: $color-font-main;
              cursor: pointer;
              display: inline-block;
            }
          }

          .count {
            width: 7px;
            height: 14px;
            font-family: PT Sans, sans-serif;
            font-size: 12px;
            font-weight: 400;
            line-height: 14px;
            text-align: right;
            color: $color-font-second;
          }
        }
      }
    }
  }
}
</style>
