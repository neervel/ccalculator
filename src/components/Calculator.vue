<template>
  <div class="calc-block">
    <div class="calc-inputs">
      <div class="calc-inputs-header">
        <span>Ингредиент</span>
        <span>Ккал</span>
        <span>Белки</span>
        <span>Жиры</span>
        <span>Углеводы</span>
        <span>Грамм</span>
      </div>
      <div class="calc-inputs-items"></div>
       <div class="calc-inputs-item" v-for="item in products" :key="item.id">
        <input type="text" v-model="item.name">
        <input type="number" placeholder="0" min="0" step="1" v-model="item.k">
        <input type="number" placeholder="0" min="0" step="1" v-model="item.b">
        <input type="number" placeholder="0" min="0" step="1" v-model="item.g">
        <input type="number" placeholder="0" min="0" step="1" v-model="item.u">
        <input type="number" placeholder="0" min="0" step="1" v-model="item.gr">
      </div>
      <button class="calc-add" @click="addItem()">+</button>
      <!-- <div class="calc-inputs-total">
        <span>Ккал: {{totalCcal}}</span>
        <span>Белки: {{totalBel}}</span>
        <span>Жиры: {{totalGir}}</span>
        <span>Углеводы: {{totalUgl}}</span>
        <span>Вес: {{totalWeight}}</span>
      </div> -->
      <div class="calc-inputs-weight">
        <label for="total-weight">Вес готового блюда, гр</label>
        <input id="total-weight" type="number" min="0" step="1" placeholder="0" v-model="readyWeight">
      </div>
      <div class="calc-inputs-total" v-show="readyWeight > 0">
        <span>Ккал: {{ccal}}</span>
        <span>Белки: {{belks}}</span>
        <span>Жиры: {{gir}}</span>
        <span>Углеводы: {{ugl}}</span>
      </div>
    </div>
    <div class="calc-result"></div>
  </div>
</template>

<script lang="ty">

export default {
  name: 'Calculator',
  data() {
    return{
      products: [
        {
          name: '',
          k: '',
          b: '',
          g: '',
          u: '',
          gr: '',
          id: 0
        }
      ],
      readyWeight: ''
    }
  },
  computed: {
    totalWeight() {
      let sum = 0
      this.products.forEach(item => { sum += Number(item.gr) })
      return sum
    },
    totalBel() {
      let sum = 0
      this.products.forEach(item => { sum += Number(item.b) })
      return sum
    },
    totalGir() {
      let sum = 0
      this.products.forEach(item => { sum += Number(item.g) })
      return sum
    },
    totalUgl() {
      let sum = 0
      this.products.forEach(item => { sum += Number(item.u) })
      return sum
    },
    totalCcal() {
      let sum = 0
      this.products.forEach(item => { sum += Number(item.k) })
      return sum
    },
    coefficient() {
      let coef = (Number(this.readyWeight) / this.totalWeight).toFixed(1)
      return Number(coef)
    },
    ccal() {
      return Number(this.totalCcal * this.coefficient).toFixed(0)
    },
    belks() {
      return Number(this.totalBel * this.coefficient).toFixed(0)
    },
    gir() {
      return Number(this.totalGir * this.coefficient).toFixed(0)
    },
    ugl() {
      return Number(this.totalUgl * this.coefficient).toFixed(0)
    }
  },
  methods: {
    addItem() {
      this.products.push({
        name: '',
        k: '',
        b: '',
        g: '',
        u: '',
        gr: '',
        id: this.products.length + 1,
      })
    }
  }
}

</script>

<style lang="sass" scoped>
  .calc
    &-block
      display: flex
      align-items: center
      justify-content: center
      margin-top: 60px
    &-inputs
      &-header
        margin-bottom: 20px
        & span
          width: 100px
          display: inline-block
          margin: 0 15px
      &-total
        margin-left: 130px
        & span
          display: inline-block
          margin: 0 15px
          width: 100px
</style>