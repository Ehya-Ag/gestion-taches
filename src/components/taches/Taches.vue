<script setup>
import { ref } from "vue";
import { useTaskStore } from "../../stores/gestion";
import TaskDetails from "./DetailsTache.vue";
import ModifierTache from "./ModifierTache.vue";
import AddTache from "./AjouterTache.vue";

const taskStore = useTaskStore();
const tasks = taskStore.tasks;
const selectedTask = ref(null);
const taskToEdit = ref(null);
const isAddingTask = ref(false);

const showDetails = (task) => {
  selectedTask.value = task;
};

const closeDetails = () => {
  selectedTask.value = null;
};

const editTask = (task) => {
  taskToEdit.value = { ...task };
};

const updateTask = (updatedTask) => {
  const index = tasks.findIndex((t) => t.id === updatedTask.id);
  if (index !== -1) {
    tasks[index] = updatedTask;
  }
  closeEdit();
};

const closeEdit = () => {
  taskToEdit.value = null;
};

const removeTask = (index) => {
  taskStore.removeTask(index);
};

const showAddTaskForm = () => {
  isAddingTask.value = true;
};

const addTask = (newTask) => {
  taskStore.addTask(newTask);
  closeAddTask();
};

const closeAddTask = () => {
  isAddingTask.value = false;
};
</script>

<template>
  <div class="container mt-4">
    <h2 class="mb-4">Liste des Tâches</h2>

    <div class="table-container">
      <table class="table table-striped table-bordered table-responsive">
        <thead class="table-dark">
          <tr>
            <th>Nom</th>
            <th>Description</th>
            <th>Date de Début</th>
            <th>Date de Fin</th>
            <th>Projet</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(task, index) in tasks" :key="task.id">
            <td>{{ task.name }}</td>
            <td>{{ task.description }}</td>
            <td>{{ task.startDate }}</td>
            <td>{{ task.endDate }}</td>
            <td>{{ task.project }}</td>
            <td>
              <button @click="showDetails(task)" class="btn btn-info btn-sm me-2">
                <i class="bi bi-eye"></i>
              </button>
              <button @click="editTask(task)" class="btn btn-warning btn-sm me-2">
                <i class="bi bi-pencil"></i>
              </button>
              <button @click="removeTask(index)" class="btn btn-danger btn-sm">
                <i class="bi bi-trash"></i>
              </button>
            </td>
          </tr>
          <tr v-if="tasks.length === 0">
            <td colspan="7" class="text-center">Aucune tâche disponible.</td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- Bouton pour afficher/masquer le formulaire d'ajout -->
    <button @click="showAddTaskForm" class="btn btn-success mt-4">
      {{ isAddingTask ? 'Annuler' : 'Ajouter une Tâche' }}
    </button>

    <!-- Affichage conditionnel des composants -->
    <ModifierTache v-if="taskToEdit" :task="taskToEdit" :onUpdate="updateTask" :onClose="closeEdit" />
    <TaskDetails v-if="selectedTask" :task="selectedTask" :onClose="closeDetails" />
    <AddTache v-if="isAddingTask" :onAdd="addTask" :onClose="closeAddTask" />
  </div>
</template>

<style scoped>
/* Styles inchangés */
</style>
