<template>
    <v-list-item
        @click="$store.commit('doneTask', task.id)"
        :class="{ 'blue lighten-4' : task.done}"
        >
        <template v-slot:default>
        <v-list-item-action>
            <v-checkbox 
            :input-value="task.done">
            </v-checkbox>
        </v-list-item-action>

        <v-list-item-content>
            <v-list-item-title
            :class="{ 'text-decoration-line-through' : task.done }"
            >
            {{ task.title }}
            </v-list-item-title>            
        </v-list-item-content>
        <v-list-item-action>
        <v-btn
        @click.stop="$store.commit('deleteTask', task.id)"
        icon
        >
        <v-icon color="primary">mdi-delete</v-icon>
        </v-btn>
        </v-list-item-action>
        </template>
    </v-list-item>  
</template>

<script>
  export default {
      props: ['task']

  }
</script>

<style>

</style>