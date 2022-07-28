<template>
  <div class="container">
    <input type="text" placeholder="add details" v-model="itemInputText">
  </div>
</template>

<script>
import store from '@/store'
export default {
  name: 'NewItemInput',
  watch: {
    itemInputText: function() {
      store.state.itemInputText = this.itemInputText
    }
  },
  computed: {
    itemInputText: {
      get() {
        return this.$store.state.itemInputText
      },
      set(value) {
        this.$store.state.itemInputText = value
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
  width: 100%;
  padding: 0.8rem 0.6rem;
  border-radius: 12px;
  border: 1px solid rgb(198, 198, 198);
}
</style>
