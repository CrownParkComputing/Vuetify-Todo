<template>
      <v-list class="pt=0"
     flat>
        <this-task 
        v-for="task in $store.state.tasks"
        :key="task.id"
        :task="task"/>
        <v-divider></v-divider>
    </v-list>
</template>

<script>
import Task from '@/components/ToDo/Task.vue'

export default {
  components: {
    'this-task': Task,
    }
}

</script>

<style>

</style>