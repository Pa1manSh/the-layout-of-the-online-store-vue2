<template>
  <div class="main-container">
    <AppFilter />
    <CardList />
  </div>
</template>

<script>
import AppFilter from "./AppFilter.vue";
import CardList from "./CardList.vue";

export default {
  name: "MainComponent",
  components: {
    AppFilter,
    CardList,
  },
};
</script>

<style lang="scss" scoped>
.main-container {
  max-width: 1720px;
  height: 1132px;
  gap: 36px;
  margin: 0 auto;
  display: flex;

  @media (max-width: 1440px) {
    max-width: 1240px;
    height: 1164px;
    gap: 36px;
  }
  @media (max-width: 375px) {
    max-width: 100%;
    height: auto;
    padding: 0px 16px;
    gap: 16px;
  }
}
</style>
