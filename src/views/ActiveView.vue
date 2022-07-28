<template>
  <div class="active">
    <div class="input-container">
      <new-item-input/>
      <add-btn/>
    </div>
    <item-component class="item" v-for="item in items.list.filter(this.filterCompleted)" :key="item.id" :itemText="item.text" :completed="item.completed" :id="item.id"/>
  </div>
</template>

<script>
// @ is an alias to /src
import NewItemInput from '@/components/newItemInput.vue'
import AddBtn from '@/components/addBtn.vue'
import ItemComponent from '@/components/itemComponent.vue'
import store from '@/store'

export default {
  name: 'ActiveView',
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
  methods: {
    filterCompleted: function(item) {
      return !item.completed
    }
  }
}
</script>

<style scoped>
.active {
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
