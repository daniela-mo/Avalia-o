<template>
  <div>
    <div class="home container">
      <div class="container__input">
        <input type="text" placeholder="Pesquise por nome ou skills" />
      </div>
    </div>
    <List />
  </div>
</template>

<script>
import List from "@/components/List.vue";

export default {
  components: {
    List,
  },
};
</script>
<style lang="scss" scoped>
.container {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  &__input {
    display: flex;
    align-items: center;
    background: #fff;
    width: 100%;
    height: 80px;
    input {
      width: 100%;
      border: none;
      outline: none;
      margin-left: 30px;
      font-size: 12px;
    }
  }
}
</style>
