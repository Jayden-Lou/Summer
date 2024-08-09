<template>
  <div class="row justify-center">
    <q-table
      flat bordered
      title="Treats"
      :rows="rows"
      :columns="columns"
      row-key="id"
      :filter="filter"
      :loading="loading"
      style="max-width: 95vw"
      class="full-width"
    >

      <template v-slot:top>
        <div class="row justify-end full-width">

        <q-input dense debounce="300" color="primary" v-model="filter">
          <template v-slot:append>
            <q-icon name="search" />
          </template>
        </q-input>
        </div>
      </template>

    </q-table>
  </div>
</template>

<script>
import { ref } from 'vue'

const columns = [
  {
    name: 'name',
    required: true,
    label: 'Dessert (100g serving)',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'calories', align: 'center', label: 'Calories', field: 'calories', sortable: true },
  { name: 'fat', label: 'Fat (g)', field: 'fat', sortable: true },
  { name: 'carbs', label: 'Carbs (g)', field: 'carbs' },
  { name: 'protein', label: 'Protein (g)', field: 'protein' },
  { name: 'sodium', label: 'Sodium (mg)', field: 'sodium' },
  { name: 'calcium', label: 'Calcium (%)', field: 'calcium', sortable: true, sort: (a, b) => parseInt(a, 10) - parseInt(b, 10) },
  { name: 'iron', label: 'Iron (%)', field: 'iron', sortable: true, sort: (a, b) => parseInt(a, 10) - parseInt(b, 10) }
]

const originalRows = [
    {
      "name": "Greek Yogurt",
      "calories": 100,
      "fat": 0.7,
      "carbs": 6,
      "protein": 10,
      "sodium": 50,
      "calcium": "15%",
      "iron": "0%"
    },
    {
      "name": "Vanilla Ice Cream",
      "calories": 207,
      "fat": 11.0,
      "carbs": 24,
      "protein": 3.5,
      "sodium": 60,
      "calcium": "8%",
      "iron": "1%"
    },
    {
      "name": "Strawberry Smoothie",
      "calories": 130,
      "fat": 2.0,
      "carbs": 28,
      "protein": 3.0,
      "sodium": 20,
      "calcium": "10%",
      "iron": "2%"
    },
    {
      "name": "Chocolate Pudding",
      "calories": 150,
      "fat": 5.0,
      "carbs": 25,
      "protein": 2.0,
      "sodium": 170,
      "calcium": "4%",
      "iron": "3%"
    },
    {
      "name": "Almond Milk Yogurt",
      "calories": 120,
      "fat": 4.5,
      "carbs": 16,
      "protein": 2.0,
      "sodium": 70,
      "calcium": "25%",
      "iron": "1%"
    },
    {
      "name": "Coconut Sorbet",
      "calories": 160,
      "fat": 7.0,
      "carbs": 25,
      "protein": 1.0,
      "sodium": 50,
      "calcium": "0%",
      "iron": "0%"
    },
    {
      "name": "Raspberry Parfait",
      "calories": 140,
      "fat": 3.0,
      "carbs": 24,
      "protein": 5.0,
      "sodium": 30,
      "calcium": "12%",
      "iron": "1%"
    },
    {
      "name": "Peach Frozen Yogurt",
      "calories": 150,
      "fat": 4.0,
      "carbs": 26,
      "protein": 4.5,
      "sodium": 60,
      "calcium": "10%",
      "iron": "1%"
    },
    {
      "name": "Mango Sorbet",
      "calories": 130,
      "fat": 1.0,
      "carbs": 32,
      "protein": 1.0,
      "sodium": 15,
      "calcium": "0%",
      "iron": "0%"
    },
    {
      "name": "Matcha Ice Cream",
      "calories": 180,
      "fat": 9.0,
      "carbs": 24,
      "protein": 4.0,
      "sodium": 70,
      "calcium": "8%",
      "iron": "2%"
    },
  {
    name: 'Frozen Yogurt',
    calories: 159,
    fat: 6.0,
    carbs: 24,
    protein: 4.0,
    sodium: 87,
    calcium: '14%',
    iron: '1%'
  },
  {
    name: 'Ice cream sandwich',
    calories: 237,
    fat: 9.0,
    carbs: 37,
    protein: 4.3,
    sodium: 129,
    calcium: '8%',
    iron: '1%'
  },
  {
    name: 'Eclair',
    calories: 262,
    fat: 16.0,
    carbs: 23,
    protein: 6.0,
    sodium: 337,
    calcium: '6%',
    iron: '7%'
  },
  {
    name: 'Cupcake',
    calories: 305,
    fat: 3.7,
    carbs: 67,
    protein: 4.3,
    sodium: 413,
    calcium: '3%',
    iron: '8%'
  },
  {
    name: 'Gingerbread',
    calories: 356,
    fat: 16.0,
    carbs: 49,
    protein: 3.9,
    sodium: 327,
    calcium: '7%',
    iron: '16%'
  },
  {
    name: 'Jelly bean',
    calories: 375,
    fat: 0.0,
    carbs: 94,
    protein: 0.0,
    sodium: 50,
    calcium: '0%',
    iron: '0%'
  },
  {
    name: 'Lollipop',
    calories: 392,
    fat: 0.2,
    carbs: 98,
    protein: 0,
    sodium: 38,
    calcium: '0%',
    iron: '2%'
  },
  {
    name: 'Honeycomb',
    calories: 408,
    fat: 3.2,
    carbs: 87,
    protein: 6.5,
    sodium: 562,
    calcium: '0%',
    iron: '45%'
  },
  {
    name: 'Donut',
    calories: 452,
    fat: 25.0,
    carbs: 51,
    protein: 4.9,
    sodium: 326,
    calcium: '2%',
    iron: '22%'
  },
  {
    name: 'KitKat',
    calories: 518,
    fat: 26.0,
    carbs: 65,
    protein: 7,
    sodium: 54,
    calcium: '12%',
    iron: '6%'
  }
]

export default {
  setup () {
    const loading = ref(false)
    const filter = ref('')
    const rowCount = ref(10)
    const rows = ref([...originalRows])

    return {
      columns,
      rows,

      loading,
      filter,
      rowCount,


    }
  }
}
</script>
