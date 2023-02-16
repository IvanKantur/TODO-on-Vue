/* eslint-disable */
<template>
  <div>
    <input type="text" v-model="todoText" placeholder="Ваша задача">
    <button @click="add" :disabled="!todoText">Добавить задачу</button>
    <button @click="deleteAll" :disabled="items.length === 0">Удалить всё</button>
    <div v-for="(item, key) in items" :key="key" class="todo-list">
      <span>{{ key + 1 }} - {{ item.text }}</span>
      <button @click="deleteEl(key)"> X </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoView',
  data () {
    return {
      todoText: '',
      items: []
    }
  },
  methods: {
    add () {
      this.items.push({ text: this.todoText })
      this.todoText = null
    },
    deleteAll () {
      this.items = []
    },
    deleteEl (key) {
      this.items.splice(key, 1)
    }
  }
}
</script>

<style scoped>

</style>
