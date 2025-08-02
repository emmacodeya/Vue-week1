<script setup>
import { ref } from 'vue'

const drinks = ref([
  { id: 'A001', name: '珍珠奶茶', describe: '香濃奶茶搭配QQ珍珠', price: 50, stock: 20 },
  { id: 'A002', name: '冬瓜檸檬', describe: '清新冬瓜配上新鮮檸檬', price: 45, stock: 18 },
  { id: 'A003', name: '翡翠檸檬', describe: '綠茶與檸檬的完美結合', price: 55, stock: 34 },
  { id: 'A004', name: '四季春茶', describe: '香醇四季春茶，回甘無比', price: 45, stock: 10 },
  { id: 'A005', name: '阿薩姆奶茶', describe: '阿薩姆紅茶搭配香醇鮮奶', price: 50, stock: 25 },
  { id: 'A006', name: '檸檬冰茶', describe: '檸檬與冰茶的清新組合', price: 45, stock: 20 },
  { id: 'A007', name: '芒果綠茶', describe: '芒果與綠茶的獨特風味', price: 55, stock: 18 },
  { id: 'A008', name: '抹茶拿鐵', describe: '抹茶與鮮奶的絕配', price: 60, stock: 20 },
])

const increaseStock = (drink) => {
  drink.stock++
}

const decreaseStock = (drink) => {
  if (drink.stock > 0) {
    drink.stock--
  }
}
</script>

<template>
  <table>
    <thead>
      <tr>
        <th scope="col">品項</th>
        <th scope="col">描述</th>
        <th scope="col">價格</th>
        <th scope="col">庫存</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="drink in drinks" :key="drink.id">
        <div class="cell-wrapper">
          <input v-model="drink.name" />
        </div>
        <td>
          <small>{{ drink.describe }}</small>
        </td>
        <td>{{ drink.price }}</td>
        <td>
          <button @click="decreaseStock(drink)">-</button>
          {{ drink.stock }}
          <button @click="increaseStock(drink)">+</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
table {
  border-collapse: collapse;
  width: 50%;
  margin: 20px auto;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  overflow: hidden;
  background-color: #fff;
}

th {
  background-color: #f4f4f4;
  font-weight: bold;
  font-size: 16px;
  padding: 12px;
  border-bottom: 2px solid #ddd;
  text-align: center;
}

td {
  font-size: 15px;
  border-bottom: 1px solid #eee;
  padding: 0;
  text-align: center;
  vertical-align: middle;
}

tr:hover {
  background-color: #f9f9f9;
}

.cell-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  padding: 10px;
  box-sizing: border-box;
}

.cell-wrapper input {
  height: 36px;
  padding: 6px 10px;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 14px;
  text-align: center;
  width: 100%;
  max-width: 160px;
  box-sizing: border-box;
}

th:nth-child(1),
td:nth-child(1) {
  width: 20%;
}

th:nth-child(2),
td:nth-child(2) {
  width: 40%;
}

th:nth-child(3),
td:nth-child(3),
th:nth-child(4),
td:nth-child(4) {
  width: 20%;
}

button {
  padding: 4px 10px;
  margin: 0 4px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 14px;
}

button:hover {
  background-color: #45a049;
}

td:last-child {
  white-space: nowrap;
}
</style>
