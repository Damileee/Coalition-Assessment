<template>
    <div class="bg-white rounded-2xl pl-2 pr-1 py-8 w-[367px] h-[720px]">
      <div class="flex items-center justify-between mb-3 pr-4">
        <p class="text-2xl font-bold">Patients</p>
        <img src="../assets/searchIcon.svg" alt="searchIcon">
      </div>
      <div class="h-[634px] overflow-y-scroll custom-scrollbar cursor-pointer pr-2">
        <div v-for="patient in patients" :key="patient.name"
             :class="['flex items-center justify-between py-2 px-3 border-b border-gray-200', { 'bg-[#D8FCF7]': isSelected(patient) }]"
             @click="selectPatient(patient)">
          <img :src="patient.profile_picture" alt="Profile Picture" class="rounded-full w-10 h-10">
          <div class="flex-1 ml-4">
            <h4 class="text-lg font-semibold">{{ patient.name }}</h4>
            <p class="text-sm text-gray-600">{{ patient.gender }}, {{ patient.age }}</p>
          </div>
          <button class="text-xl text-gray-500"><img src="../assets/moreHorizIcon.svg" alt="More Options Icon"></button>
        </div>
      </div>
    </div>
</template>
  
<script>
  export default {
    name: 'PatientList',
    props: {
      patients: {
        type: Array,
        required: true
      },
      selectedPatient: {
        type: Object,
        required: true
      }
    },
    methods: {
      selectPatient(patient) {
        this.$emit('selectPatient', patient);
      },
      isSelected(patient) {
        return patient === this.selectedPatient;
      }
    }
  }
</script>
  
<style scoped>
  .custom-scrollbar::-webkit-scrollbar {
    width: 6px;
  }
  
  .custom-scrollbar::-webkit-scrollbar-track {
    background: #f1f1f1;
    border-radius: 10px;
  }
  
  .custom-scrollbar::-webkit-scrollbar-thumb {
    background: #888;
    border-radius: 10px;
  }
  
  .custom-scrollbar::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
</style>  