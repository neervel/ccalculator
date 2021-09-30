<template>
  <div class="calc-block">
    <div class="calc-inputs">
      <div class="calc-inputs-header">
        <span>Ингредиент</span>
        <span>Ккал</span>
        <span>Белки</span>
        <span>Жиры</span>
        <span>Углеводы</span>
      </div>
      <div class="calc-inputs-item">
        <input type="text">
        <input type="number" value="0" min="0" step="0.1">
        <input type="number" value="0" min="0" step="0.1">
        <input type="number" value="0" min="0" step="0.1">
        <input type="number" value="0" min="0" step="0.1">
      </div>
    </div>
    <div class="calc-result"></div>
  </div>
</template>

<script>
export default {
  name: 'Calculator'
}
</script>