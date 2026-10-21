<template>
  <div id="app">
    <div class="title-section">SPENT</div>
    <div class="filter-section"></div>
    <div class="graph-section"></div>
    <div class="list-section">
      <div class="list-item" v-for="item in transactionRecordList">
        <div class="item-title">{{ item.category }}</div>
        <div class="item-amount">{{ item.amount }}</div>
        <div class="item-date">{{ item.date }}</div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface transactionRecordItem {
  id: number
  dateTime: string
  category: string
  amount: number
}

const transactionRecordList = ref<transactionRecordItem[]>([])

const getTransactionSummary = async () => {
  const response = [
    {
      id: 1,
      dateTime: '2026-01-01',
      category: 'Food',
      amount: 100,
    },
    {
      id: 2,
      dateTime: '2026-01-02',
      category: 'Transport',
      amount: 200,
    },
    {
      id: 3,
      dateTime: '2026-01-03',
      category: 'Entertainment',
      amount: 1590,
    },
  ]
  transactionRecordList.value = response
}

const deleteRecord = (id: number) => {
  transactionRecordList.value = transactionRecordList.value.filter((item) => item.id !== id)
}

onMounted(async () => {
  await getTransactionSummary()
})
</script>

<style scoped lang="scss">
#app {
  width: 100%;
  min-height: 100vh;
  padding: 20px;

  .list-section {
    .list-item {
      outline: auto;
    }
  }
}
</style>
