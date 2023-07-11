<template>
    <div class="warning" role="warning">
      <h2>Warning</h2>
        <slot> </slot>
    </div>
</template>

<style scoped>
.warning {
  color: orange;
  font-weight: bold;
}
</style>