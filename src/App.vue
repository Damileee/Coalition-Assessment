<template>
  <div>
    <Nav />
    <main class="flex justify-between mt-6">
      <aside>
        <PatientList :patients="patients" :selectedPatient="selectedPatient" @selectPatient="selectPatient" />
      </aside>

      <section>
        <DiagnosisHistory 
          :patient="selectedPatient"
        />
        <DiagnosticList v-if="selectedPatient" :diagnosticList="selectedPatient.diagnostic_list" class="mt-6"/>
      </section>

      <aside>
        <PatientInfo v-if="selectedPatient" :patient="selectedPatient" />
        <LabResults v-if="selectedPatient" :labResults="selectedPatient.lab_results" class="mt-6"/>
      </aside>
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

import Nav from './components/Nav.vue';
import PatientList from './components/PatientList.vue';
import DiagnosisHistory from './components/DiagnosisHistory.vue';
import DiagnosticList from './components/DiagnosticList.vue';
import PatientInfo from './components/PatientInfo.vue';
import LabResults from './components/LabResults.vue';

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
    selectedPatient.value = patients.value[3]; // Adjust this based on your logic
  } catch (error) {
    console.error('Error fetching patient data:', error);
  }
};

const selectPatient = (patient) => {
  selectedPatient.value = patient;
};

onMounted(fetchPatientData());
</script>