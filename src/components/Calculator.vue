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
      <div class="calc-inputs-total">
        <span>Ккал: {{totalCcal}}</span>
        <span>Белки: {{totalBel}}</span>
        <span>Жиры: {{totalGir}}</span>
        <span>Углеводы: {{totalUgl}}</span>
        <span>Вес: {{totalWeight}}</span>
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
      ]
    }
  },
  computed: {
    totalWeight() {
      let sum = 0
      this.products.forEach(item => {
        sum += Number(item.gr)
      })
      return Number(sum)
    },
    totalBel() {
      let sum = 0
      this.products.forEach(item => {
        sum += Number(item.b)
      })
      return Number(sum)
    },
    totalGir() {
      let sum = 0
      this.products.forEach(item => {
        sum += Number(item.g)
      })
      return Number(sum)
    },
    totalUgl() {
      let sum = 0
      this.products.forEach(item => {
        sum += Number(item.u)
      })
      return Number(sum)
    },
    totalCcal() {
      let sum = 0
      this.products.forEach(item => {
        sum += Number(item.k)
      })
      return Number(sum)
    }
  },
  methods: {
    addItem() {
      let i = this.products.length
      this.products.push({
        name: '',
          k: '',
          b: '',
          g: '',
          u: '',
          gr: '',
          id: i+1,
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
      &-item
        & input
          width: 100px
          display: inline-block
          padding: 0
          margin: 0
          border: none
          border-bottom: 1px solid #000
          margin: 0 15px
          padding: 5px 10px
          font-size: 18px
          &:focus
            outline: none
      &-total
        margin-left: 130px
        & span
          display: inline-block
          margin: 0 15px
          width: 100px
</style>