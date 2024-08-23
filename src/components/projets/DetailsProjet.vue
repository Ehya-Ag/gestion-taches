<template>
    <div class="details-container">
      <!-- <button class="btn-close" @click="closeDetails">×</button> -->
      <h2>Détails du Projet</h2>
      <div v-if="project">
        <p><strong>Nom:</strong> {{ project.name }}</p>
        <p><strong>Date de Début:</strong> {{ project.startDate }}</p>
        <p><strong>Date de Fin:</strong> {{ project.endDate }}</p>
      </div>
      <div v-else>
        <p>Projet non trouvé.</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { computed } from 'vue';
  import { useProjectStore } from '../../stores/gestion';
  
  const props = defineProps({
    projectId: Number,
    onClose: {
      type: Function,
      required: true,
    },
  });

 
  const projectStore = useProjectStore();
  const project = computed(() => projectStore.getProjectById(props.projectId));
  
  const closeDetails = () => {
    props.onClose();
  };
  </script>
  
  <style scoped>
  .details-container {
    background: #f8f9fa;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    padding: 20px;
    max-width: 600px;
    margin: auto;
    margin-top: 20px;
    position: relative;
    z-index: 1;
  }
  
  .btn-close {
    position: absolute;
    top: 10px;
    right: 10px;
    background: #dc3545;
    color: #fff;
    border: none;
    border-radius: 50%;
    width: 30px;
    height: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    cursor: pointer;
  }
  
  .btn-close:hover {
    background: #c82333;
  }
  </style>
  