<template>
  <div class="container">
    <button @click="addActive">Add</button>
  </div>
</template>

<script>
import store from '@/store'
export default {
  name: 'addBtn',
  props: {
    
  },
  methods: {
    addActive() {
      store.state.items.list.push({
        id: store.state.items.idCount,
        text: store.state.itemInputText,
        completed: false
      })
      store.state.items.idCount++
      store.state.itemInputText = ''

      localStorage.setItem('items', JSON.stringify(store.state.items))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  float: right;
  padding: 0.8rem 2rem;
  color: white;
  background: rgb(33, 101, 228);
  border: none;
  border-radius: 12px;
}
</style>
