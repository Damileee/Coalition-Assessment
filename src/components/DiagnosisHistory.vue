<template>
  <div class="bg-white rounded-lg p-6 w-[766px]">
    <div class="flex items-center justify-between mb-6">
      <h2 class="text-2xl font-bold">Diagnosis History</h2>
    </div>
    <div v-if="patient">
      <div class="grid grid-col gap-4 lg:grid-col">
        <div class="bg-purple-50 p-4 rounded-lg flex gap-12">
          <div>
            <div class="flex justify-between items-center mb-4">
              <h3 class="text-lg font-bold">Blood Pressure</h3>
              <select v-model="selectedTimeFrame" @change="updateChartData">
                <option value="6">Last 6 months</option>
                <option value="12">Last 12 months</option>
              </select>
            </div>
            <div>
              <Line :data="chartData" :options="chartOptions"></Line>
            </div>
          </div>
          <div class="">
            <div>
              <p class="text-pink-500 font-bold">Systolic</p>
              <p class="text-3xl font-bold">{{ systolic.value }}</p>
              <p>{{ systolic.levels }}</p>
            </div>
            <div>
              <p class="text-purple-500 font-bold">Diastolic</p>
              <p class="text-3xl font-bold">{{ diastolic.value }}</p>
              <p>{{ diastolic.levels }}</p>
            </div>
          </div>
        </div>
        <div class="grid grid-cols-1 gap-4 md:grid-cols-3">
          <div class="bg-blue-50 p-4 rounded-lg flex flex-col">
            <img src="../assets/respiratoryIcon.svg" alt="Respiratory Rate" class="mb-2">
            <p class="text-xl font-bold">{{ respiratoryRate.value }} bpm</p>
            <p>{{ respiratoryRate.levels }}</p>
          </div>
          <div class="bg-red-50 p-4 rounded-lg flex flex-col">
            <img src="../assets/temperatureIcon.svg" alt="Temperature" class="mb-2">
            <p class="text-xl font-bold">{{ temperature.value }}°F</p>
            <p>{{ temperature.levels }}</p>
          </div>
          <div class="bg-pink-50 p-4 rounded-lg flex flex-col">
            <img src="../assets/heartRateIcon.svg" alt="Heart Rate" class="mb-2">
            <p class="text-xl font-bold">{{ heartRate.value }} bpm</p>
            <p>{{ heartRate.levels }}</p>
          </div>
        </div>
      </div>
    </div>
    <div v-else>
      <p>Select a patient to view their diagnosis history.</p>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue';
import { Line } from 'vue-chartjs';
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  LineElement,
  CategoryScale,
  LinearScale,
  PointElement
} from 'chart.js';

ChartJS.register(Title, Tooltip, Legend, LineElement, CategoryScale, LinearScale, PointElement);

const props = defineProps({
  patient: Object
});

const chartOptions = ref({
  responsive: true,
  maintainAspectRatio: false,
  scales: {
    x: {
      display: true,
      title: {
        display: true,
        text: 'Month'
      }
    },
    y: {
      display: true,
      title: {
        display: true,
        text: 'Value'
      }
    }
  }
});

const chartData = ref({
  labels: [],
  datasets: [
    {
      label: 'Systolic',
      borderColor: '#FF6384',
      data: [],
      fill: false
    },
    {
      label: 'Diastolic',
      borderColor: '#36A2EB',
      data: [],
      fill: false
    }
  ]
});

const selectedTimeFrame = ref('6');
const systolic = ref({});
const diastolic = ref({});
const heartRate = ref({});
const respiratoryRate = ref({});
const temperature = ref({});

const updateChartData = () => {
  if (!props.patient || !props.patient.diagnosis_history) return;

  const history = props.patient.diagnosis_history.slice(-selectedTimeFrame.value);
  chartData.value.labels = history.map(h => `${h.month}, ${h.year}`);
  chartData.value.datasets[0].data = history.map(h => h.blood_pressure.systolic.value);
  chartData.value.datasets[1].data = history.map(h => h.blood_pressure.diastolic.value);

  const latestDiagnosis = history[history.length - 1];
  if (latestDiagnosis) {
    systolic.value = latestDiagnosis.blood_pressure.systolic;
    diastolic.value = latestDiagnosis.blood_pressure.diastolic;
    heartRate.value = latestDiagnosis.heart_rate;
    respiratoryRate.value = latestDiagnosis.respiratory_rate;
    temperature.value = latestDiagnosis.temperature;
  }
};

watch(() => props.patient, updateChartData, { immediate: true });
watch(selectedTimeFrame, updateChartData);
</script>