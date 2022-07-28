<template>
  <div class="container">
    <div class="left-col">
      <input type="checkbox" id="check" v-model="state">
      <label for="check" :class="completed ? 'completed' : 'active'">{{itemText}}</label>
    </div>
    <div class="right-col" @click="deleteItem"><i class="fa-solid fa-trash-can" v-if="completed"></i></div>
  </div>
</template>

<script>
import store from '@/store'
export default {
  name: 'itemComponent',
  props: {
    itemText: String,
    completed: Boolean,
    id: Number
  },
  data: function() {
    return {
      state: this.completed,
      currentId: this.id
    }
  },
  watch: {
    state: function() {
      for (const item of store.state.items.list) {
        if (item.id === this.currentId) {
          item.completed = !item.completed
          localStorage.setItem('items', JSON.stringify(store.state.items))
          return
        }
      }
    }
  },
  methods: {
    deleteItem() {
      let count = 0
      for (const item of store.state.items.list) {
        if (item.id === this.currentId) {
          store.state.items.list.splice(count, 1)
          break
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
.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.left-col {
  display: flex;
  gap: 0.5rem;
}

.right-col {
  cursor: pointer;
}

.completed {
 text-decoration: line-through;
}

.active {
  text-decoration: none;
}
</style>
