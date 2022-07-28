<template>
  <div class="container">
    <button @click="deleteAll"><i class="fa-solid fa-trash-can"></i>Delete all</button>
  </div>
</template>

<script>
import store from '@/store'
export default {
  name: 'deleteAllBtn',
  methods: {
    deleteAll() {
      let count = 0
      while (count < store.state.items.list.length) {
        if (store.state.items.list[count].completed) {
          store.state.items.list.splice(count, 1)
          continue
        }
        count++
      }
      localStorage.setItem('items', JSON.stringify(store.state.items))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  margin-top: 2rem;
  float: right;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 1rem 2rem;
  border: none;
  border-radius: 12px;
  color: white;
  background: rgb(237, 57, 57);
}
</style>
