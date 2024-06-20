<template>
  <div>
    <Nav />
    <main class="flex gap-6 mt-6">
      <aside>
        <PatientList :patients="patients" @selectPatient="selectPatient" />
      </aside>
      <section>
        <DiagnosisHistory 
          :patient="selectedPatient"
        />
      </section>
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

import Nav from './components/Nav.vue';
import PatientList from './components/PatientList.vue';
import DiagnosisHistory from './components/DiagnosisHistory.vue';

const patients = ref([]);
const selectedPatient = ref(null);

const fetchPatientData = async () => {
  try {
    const response = await axios.get('https://fedskillstest.coalitiontechnologies.workers.dev', {
      auth: {
        username: 'coalition',
        password: 'skills-test'
      }
    });
    patients.value = response.data;
    selectedPatient.value = patients.value[0]; // Default to the first patient
  } catch (error) {
    console.error('Error fetching patient data:', error);
  }
};

const selectPatient = (patient) => {
  selectedPatient.value = patient;
};

onMounted(fetchPatientData());
</script>