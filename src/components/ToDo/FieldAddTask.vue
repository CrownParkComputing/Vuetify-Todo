<template>
    <v-text-field
      v-model.trim="newTaskTitle"
        @click:prepend="addTask"
        @keyup.enter="addTask"
        class="pa-3"
        filled
        label="Add task"
        prepend-icon="mdi-plus"
        hide-details
        clearable
      ></v-text-field>
</template>

<script>
export default {
  data() {
    return {
      newTaskTitle: ''
    }
  },
  methods: {
    addTask() {
      this.$store.commit('addTask', this.newTaskTitle)
      this.newTaskTitle = ''
    }     
  }
}
</script>

<style>
</style>

