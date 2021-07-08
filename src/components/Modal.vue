<template>
  <div class="modal-all">
    <div class="modal-all__content">
      <slot />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.modal-all {
  background: rgb(15, 15, 15, 0.15);
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  &__content {
    width: 544px;
    height: 539px;
    background: #fff;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
  }
}
</style>
