<template>
  <div class="all">
    <div class="input-container">
      <new-item-input/>
      <add-btn/>
    </div>
    <item-component class="item" v-for="item in items.list" :key="item.id" :itemText="item.text" :completed="item.completed" :id="item.id"/>
  </div>
</template>

<script>
// @ is an alias to /src
import NewItemInput from '@/components/newItemInput.vue'
import AddBtn from '@/components/addBtn.vue'
import ItemComponent from '@/components/itemComponent.vue'
import store from '@/store'

export default {
  name: 'AllView',
  components: {
    NewItemInput,
    AddBtn,
    ItemComponent
  },
  data: function() {
    return {
      items: store.state.items
    }
  },
  beforeCreate() {
    if (localStorage.items) {
      store.state.items = JSON.parse(localStorage.getItem('items'))
    }
  }
}
</script>

<style scoped>
.all {
  width: 100%;
}

.input-container {
  display: grid;
  grid-template-columns: 80% 20%;
  margin-bottom: 1rem;
}

.item {
  margin-bottom: 0.5rem;
}

@media only screen and (max-width: 800px) {
  .input-container {
    grid-template-columns: 70% 20%;
    gap: 10%;
  }
}
</style>
