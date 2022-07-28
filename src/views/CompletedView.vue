<template>
  <div class="completed">
    <div class="item-container">
      <item-component class="item" v-for="item in items.list.filter(this.filterCompleted)" :key="item.id" :itemText="item.text" :completed="item.completed" :id="item.id"/>
    </div>
    <delete-all-btn/>
  </div>
</template>

<script>
// @ is an alias to /src
import ItemComponent from '@/components/itemComponent.vue'
import store from '@/store'
import DeleteAllBtn from '@/components/deleteAllBtn.vue'

export default {
  name: 'CompletedView',
  components: {
    ItemComponent,
    DeleteAllBtn
  },
  data: function() {
    return {
      items: store.state.items
    }
  },
  methods: {
    filterCompleted: function(item) {
      return item.completed
    }
  }
}
</script>

<style scoped>
.completed {
  width: 100%;
}


</style>
