<template>
  <div>
    <header class="header-container">
      <div class="logo-catalog-container">
        <div class="logo-container">
          <img src="/logo.png" alt="Logo" class="logo-image" />
          <span class="logo-text">Логотип</span>
        </div>
        <button class="catalog-button">Каталог</button>
      </div>
      <div class="search-container">
        <div class="search-inner-container">
          <img src="/search-img.png" alt="Search" class="search-icon" />

          <input
            type="text"
            placeholder="Поиск по 100 000 товаров"
            class="search-input"
            v-model="searchText"
          />
          <img
            v-if="searchText"
            src="/text-del.png"
            alt="Clear"
            class="text-clear-icon"
            @click="clearSearch"
          />
        </div>
        <button v-if="searchText" class="search-button">Найти</button>
      </div>
      <div class="navigation-block">
        <a href="#" class="navigation-link company-info"
          >Информация о компании</a
        >
        <a href="#" class="navigation-link contacts">Контакты</a>
        <a href="#" class="navigation-link useful-links">Полезные ссылки</a>
      </div>
    </header>
    <!-- Мобильный контейнер -->
    <div class="header-container-for-mobile">
      <div class="search-container-for-mobile">
        <img
          src="/arrow-icon.png"
          alt="Search"
          class="search-icon-for-mobile"
        />
        <input
          type="text"
          placeholder=""
          class="search-input-for-mobile"
          v-model="searchText"
          @focus="changeDividerColor"
          @blur="resetDividerColor"
        />
        <img
          v-if="searchText"
          src="/text-del2.png"
          alt="Clear"
          class="text-clear-icon-mobile"
          @click="clearSearch"
        />

        <button class="search-button-for-mobile">Найти</button>
      </div>
      <div class="mobile-divider">
        <img ref="mobileDivider" src="/divider.png" alt="divider" />
      </div>
      <div class="category-container-for-mobile">
        <span class="category-text-for-mobile"> Название категории</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppHeader",
  data() {
    return {
      searchText: "",
    };
  },
  methods: {
    clearSearch() {
      this.searchText = "";
    },
    changeDividerColor() {
      this.$refs.mobileDivider.src = "/divider-active.png";
    },
    resetDividerColor() {
      this.$refs.mobileDivider.src = "/divider.png";
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/variables.scss";
body,
html {
  margin: 0;
  padding: 0;
}

.header-container {
  box-sizing: border-box;
  max-width: 1720px;
  margin: 0 auto;
  height: 72px;
  padding: 12px 0;
  background: none;
  position: relative;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  margin-bottom: 10px;

  display: flex;
  justify-content: space-between;
  align-items: center;

  @media (max-width: 1440px) {
    padding: 12px 128px 12px 128px;
  }
  @media (max-width: 375px) {
    display: none;
  }
}
.logo-catalog-container {
  display: flex;
  align-items: center;
  gap: 8px;
  max-width: 257px;
  height: 48px;
}

.logo-container {
  display: flex;
  align-items: center;
  gap: 8px;
  max-width: 145px;
  height: 48px;
  padding: 0 24px;
  border-radius: 10px;
}

.logo-image {
  max-width: 24px;
  height: 24px;
  padding: 3px;
}

.logo-text {
  max-width: 65px;
  height: 19px;
  font-family: Inter, sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 19.36px;
  text-align: center;
  color: #000000;
}

.catalog-button {
  max-width: 104px;
  height: 48px;
  padding: 8px 24px;
  gap: 10px;
  border-radius: 8px;
  border: 1px solid #73aff4;
  background: transparent;
  color: #73aff4;
  font-family: Inter, sans-serif;
  font-size: 16px;
  font-weight: 400;
  cursor: pointer;
  box-sizing: border-box;
}

.search-container {
  max-width: 1015px;
  height: 48px;
  padding: 4px 16px;
  border-radius: 10px;
  border: 1px solid $color-font-second;
  transition: border-color 0.3s ease;
  display: flex;
  align-items: center;
  flex-grow: 1;
  margin-right: 20px;
  gap: 8px;
  margin-left: 20px;
  box-sizing: border-box;
  &:hover {
    border-color: #73aff4;
  }
  @media (max-width: 1440px) {
    width: 479px;
    flex-grow: 0;
  }
}

.search-inner-container {
  max-width: 983px;
  height: 24px;
  gap: 8px;

  display: flex;
  align-items: center;
  width: 100%;
  box-sizing: border-box;
}

.search-icon {
  width: 24px;
  height: 24px;
  padding: 3px 3.51px 3.51px 3px;
  box-sizing: border-box;
}

.search-input {
  max-width: 951px;
  height: 24px;
  width: 100%;
  font-family: Inter, sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 24px;
  text-align: left;
  color: #5a5a5a;
  border: none;
  outline: none;
  box-sizing: border-box;
}
.text-clear-icon {
  width: 20px;
  height: 20px;
  position: sticky;
  top: 2px;
  right: 2px;
  cursor: pointer;
  box-sizing: border-box;
}
.search-button {
  max-width: 70px;
  height: 38px;
  padding: 12px 16px;
  gap: 4px;
  border-radius: 8px;
  border: none;
  background: #73aff4;
  color: #eef1f3;
  font-family: Inter, sans-serif;
  font-size: 14px;
  font-weight: 400;
  cursor: pointer;
  position: relative;
  margin-left: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
}

.navigation-block {
  display: flex;
  gap: 20px;
}

.navigation-link {
  display: block;
  font-family: Inter, sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: 16.94px;
  text-align: left;
  color: #393939;
  text-decoration: none;

  &.company-info {
    width: 172px;
    height: 17px;
  }

  &.contacts {
    width: 65px;
    height: 17px;
  }

  &.useful-links {
    width: 123px;
    height: 17px;
  }
}
/* Стили для мобильных устройств */
.header-container-for-mobile {
  width: 100%;
  max-width: 375px;
  height: 148px;
  padding: 0px 0px 12px 0px;
  gap: 12px;
  position: relative;

  box-sizing: border-box;
  z-index: 1000;

  top: 0;
  left: 0;
  display: flex;

  right: 0;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;

  @media (min-width: 376px) {
    display: none;
  }
}

.search-container-for-mobile {
  max-width: 100%;
  height: 53px;
  padding: 8px 16px 0px 16px;
  gap: 10px;
  display: flex;
  align-items: center;
  flex-direction: row;
  box-sizing: border-box;
}

.search-input-for-mobile {
  width: 343px;
  flex: 1;
  height: 38px;
  font-family: Inter, sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 38px;
  border: none;
  outline: none;
  box-sizing: border-box;
}

.search-icon-for-mobile {
  width: 20px;
  height: 20px;
}

.text-clear-icon-mobile {
  width: 20px;
  height: 20px;
  padding: 1.67px;
  opacity: 0.3;
}

.search-button-for-mobile {
  width: 75px;
  height: 38px;
  padding: 12px 16px;
  gap: 10px;
  border-radius: 5px;
  border: none;
  background: $color-brand;
  color: white;
  font-family: "PT Sans", sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 14px;
  text-align: left;
  border: none;
  margin-left: 10px;
  cursor: pointer;
  position: relative;
  box-sizing: border-box;
}

.mobile-divider {
  max-width: 307px;
  height: 1px;
  background-size: cover;
  position: relative;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  margin-left: 50px;
  margin-right: auto;
}
.mobile-divider img {
  max-width: 100%;
  height: auto;
  display: block;
}

.search-input-for-mobile:focus ~ .mobile-divider {
  background-color: $color-brand;
}
.category-container-for-mobile {
  width: 100%;
  height: 28px;
  padding: 0px 24px;
  gap: 10px;
  display: flex;
  align-items: center;
  box-sizing: border-box;
}

.category-text-for-mobile {
  width: 195px;
  height: 28px;
  color: $color-font-main;
  font-family: "PT Sans", sans-serif;
  font-size: 22px;
  font-weight: 400;
  line-height: 28px;
  text-align: left;
  white-space: nowrap;
}
</style>
