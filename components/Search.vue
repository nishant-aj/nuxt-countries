<template>
  <div class="input-container">
    <i class="fa-solid fa-magnifying-glass icon"></i>

    <input type="text" placeholder="Search for a country..." class="input-field">
  </div>
</template>

<style scoped>
.input-container {
  display: inline-flex;
  align-items: center;
  background: white;
  box-shadow: 0 0 5px 5px #eeeeee;
}

.icon {
  padding: 10px;
  min-width: 40px;
}

.input-field {
  border: none;
  outline: none;
  padding: 8px 10px 8px 0;
}
</style>