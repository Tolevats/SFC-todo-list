<template>
  <div class="tasks">
    <h1>Lista de Tareas</h1>
    
    <!-- input y botón para agregar tareas -->
    <input v-model="newTask" placeholder="Escribe una tarea" @keyup.enter="addTask"/>
    <button @click="addTask">Agregar Tarea</button>

    <!-- lista de tareas -->
    <ul>
        <li v-for="(task, index) in tasks" :key="index">
        <div v-if="!task.isEditing">
          {{ task.name }}
          <button @click="editTask(index)">Editar</button>
          <button @click="deleteTask(index)">Borrar</button>
        </div>
        <div v-else>
          <input v-model="task.name" @keyup.enter="saveTask(index)" />
          <button @click="saveTask(index)">Guardar</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
    name: 'TodoList',
    // props: {},
    data() {
        return {
            newTask: '', //contenido de la nueva tarea
            tasks: [] //lista de tareas
        }
    },
    // computed: {},
    methods: {
      addTask() {
        //verificar si hay texto en 'nuevaTarea' antes de agregarla
        if (this.newTask.trim() !== '') {
            this.tasks.push({ name: this.newTask, isEditing: false });
            this.newTask = ''; //limpiar el input
        }
      },
      deleteTask(index) {
        //eliminar tarea del array
        this.tasks.splice(index, 1);
      },
      editTask(index) {
        //editar tarea
        this.tasks[index].isEditing = true;
      },
      saveTask(index) {
        this.tasks[index].isEditing = false;
      }
    }
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
};
</script>

<style scoped>
.tasks {
  max-width: 400px;
  margin: auto;
  text-align: center;
}
input {
  padding: 0.5rem;
  margin-right: 0.5rem;
}
button {
  padding: 0.5rem;
  margin-left: 0.5rem;
  cursor: pointer;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 10px 0;
}
</style>