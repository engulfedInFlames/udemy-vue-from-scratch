<template>
  <dialog open>
    <slot></slot>
  </dialog>
</template>

<style scoped>
dialog {
  position: fixed;
  top: 20vh;
  left: 30%;
  width: 40%;
  margin: 0;
  border: none;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  background-color: white;
}
</style>
