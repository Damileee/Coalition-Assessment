<template>
  <div class="bg-white rounded-2xl p-6 w-[900px]">
    <div class="flex items-center justify-between mb-6">
      <h2 class="text-2xl font-bold">Diagnosis History</h2>
    </div>
    <div v-if="patient">
      <div class="grid grid-col gap-4 lg:grid-col">
        <div class="bg-[#F4F0FE] p-4 rounded-2xl flex gap-12">
          <div>
            <!-- Dropdown -->
            <div class="flex justify-between items-center mb-4">
              <h3 class="text-lg font-bold">Blood Pressure</h3>
              <select class="bg-[#F4F0FE]" v-model="selectedTimeFrame" @change="updateChartData">
                <option value="6">Last 6 months</option>
                <option value="12">Last 12 months</option>
              </select>
            </div>

            <!-- Line chart -->
            <div class="w-[550px] h-[150px]">
              <Line :chart-data="chartData" :chart-options="chartOptions" class="w-[550px] h-[150px]"></Line>
            </div>
          </div>

          <!-- Blood Pressure Indicator -->
          <div>
            <BloodPressureIndicator
              label="Systolic"
              :value="systolic.value"
              :levels="systolic.levels"
              color="bg-[#E66FD2]"
              isBorderBottom
            />
            <BloodPressureIndicator
              label="Diastolic"
              :value="diastolic.value"
              :levels="diastolic.levels"
              color="bg-[#8C6FE6]"
            />
          </div>
        </div>

        <!-- VitalSign section -->
        <div v-if="patient">
          <div class="grid grid-cols-1 gap-4 md:grid-cols-3">
            <VitalSign
              :icon="RespiratoryIcon"
              title="Respiratory Rate"
              :value="respiratoryRate.value + ' bpm'"
              :levels="respiratoryRate.levels"
              wrapperClass="bg-[#E0F3FA] p-4 rounded-2xl flex flex-col"
            />
            <VitalSign
              :icon="TemperatureIcon"
              title="Temperature"
              :value="temperature.value + '°F'"
              :levels="temperature.levels"
              wrapperClass="bg-[#FFE6E9] p-4 rounded-2xl flex flex-col"
            />
            <VitalSign
              :icon="HeartRateIcon"
              title="Heart Rate"
              :value="heartRate.value + ' bpm'"
              :levels="heartRate.levels"
              wrapperClass="bg-[#FFE6F1] p-4 rounded-2xl flex flex-col"
            />
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
import { computed, ref, watch } from 'vue';
import VitalSign from './VitalSign.vue';
import BloodPressureIndicator from './BloodPressureIndicator.vue';
import RespiratoryIcon from '../components/icons/RespiratoryIcon.vue'
import TemperatureIcon from '../components/icons/TemperatureIcon.vue';
import HeartRateIcon from '../components/icons/HeartRateIcon.vue';
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
        display: false,
      }
    },
    y: {
      display: true,
      title: {
        display: false,
      }
    }
  }
});

const selectedTimeFrame = ref('6');
const systolic = ref({});
const diastolic = ref({});
const heartRate = ref({});
const respiratoryRate = ref({});
const temperature = ref({});

const systolicData = computed(() => {
  const history = props.patient?.diagnosis_history ?? [];
  return history.map(h => h.blood_pressure.systolic.value);
});

const diastolicData = computed(() => {
  const history = props.patient?.diagnosis_history;
  return history.map(h => h.blood_pressure.diastolic.value);
});

const chartData = ref({
  labels: [],
  datasets: [
    {
      label: 'Systolic',
      borderColor: '#E66FD2',
      tension: 0.4,
      data: systolicData.value,
      fill: false
    },
    {
      label: 'Diastolic',
      borderColor: '#8C6FE6',
      tension: 0.4,
      data: diastolicData.value,
      fill: false
    }
  ]
});

const updateChartData = () => {
  if (!props.patient || !props.patient.diagnosis_history) return;

  const history = props.patient.diagnosis_history.slice(-selectedTimeFrame.value);
  chartData.value.labels = history.map(h => h.month);
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
</script>./icons/HeartRateIcon.vue./icons/RespiratoryIcon.vue./icons/TemperatureIcon.vue