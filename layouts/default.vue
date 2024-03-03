<template>
    <div class="body">
        <TheHeader />
        <div class="main">
          <slot/>
        </div>
        <TheFooter />
    </div>
</template>
<script setup lang="ts">
</script>
<style scoped lang="scss">
  .body {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  .main {
    flex: 1;
  }
</style>
