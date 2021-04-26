<template>
  <div class="home">

    <v-text-field
      v-model="newTaskTitle"
        @click:append="addTask"
        @keyup.enter="addTask"
        class="pa-3"
        filled
        label="Add task"
        append-icon="mdi-plus"
        hide-details
        clearable
      ></v-text-field>


    <v-list
     v-if="tasks.length"
     class="pt=0"
     flat
     >
     <div
       v-for="task in tasks"
       :key="task.id"
       >
        <v-list-item
          @click="doneTask(task.id)"
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
          @click.stop="deleteTask(task.id)"
          icon
          >
            <v-icon color="primary">mdi-delete</v-icon>
          </v-btn>
          </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider></v-divider>
     </div>
    </v-list>
    <div
      v-else
    >
      <v-icon
        size="100"
        color="primary"
        >
        mdi-check
      </v-icon>
      <div
        class="text-h5 primary--text"> No Tasks</div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data() {
    return {
      newTaskTitle: '',
      tasks: [
        {
          id: 1, 
          title: 'Wake Up',
          done: false
        },
        {
          id: 2,
          title: 'Take Tablets',
          done: false
        },
        {
          id: 3,
          title: 'Eat Breakfast',
          done: false
        },
        {
          id: 4,
          title: 'Walk dogs', 
          done: false
        }
      ]
    }
  },
  methods: {
    addTask() {
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false,
      }
      this.tasks.push(newTask)
      this.newTaskTitle = ''
    },
    doneTask(id){
      let task = this.tasks.filter(task => task.id === id)[0]  
      task.done = !task.done 
    }, 
    deleteTask(id){
      this.tasks = this.tasks.filter(task => task.id !== id) 
    } 
  }
}
</script>
