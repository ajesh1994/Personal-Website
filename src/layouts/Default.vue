<template>
  <div class="layout">
    <div class="container">
      <div class="header">
        <Articles />
        <NavBar />
      </div>
      <slot />
      <FootBar />
    </div>
  </div>
</template>

<style scoped>
.header {
  background: #f5f5f5;
  position: relative;
}
</style>
