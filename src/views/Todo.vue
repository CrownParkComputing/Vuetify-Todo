<template>
  <div class="home">
    <field-add-task
    />

    <list-tasks 
      v-if="$store.state.tasks.length"
    />
    <div
      v-else
      class="no-tasks"
    >
      <v-icon
        size="100"
        color="primary"
        >
        mdi-check
      </v-icon>
      <div
        class="text-h5 primary--text">No Tasks</div>
    </div>
  </div>
</template>

<script>
import FieldAddTask from '@/components/ToDo/FieldAddTask.vue'
import ListTasks from '@/components/ToDo/ListTasks.vue'

export default {
  name: 'Home',
  components: {
    'field-add-task': FieldAddTask,
    'list-tasks': ListTasks
    }
}

</script>

<style lang="sass">
.no-tasks
  position: absolute
  left: 50%
  top: 50%
  transform: translate(-50%, -50%)
  opacity: 0.5
</style>
