<template>
  <div class="modal-global">
    <div class="modal-global__content">
      <slot />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.modal-global {
  background: rgba(15, 15, 15, 0.15);
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  position: fixed;
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
