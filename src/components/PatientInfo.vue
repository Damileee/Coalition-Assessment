<template>
    <div class="bg-white rounded-2xl p-6 w-96">
      <div class="flex flex-col items-center mb-6">
        <img :src="patient.profile_picture" alt="Profile Picture" class="rounded-full w-[200px] h-[200px] mb-4" />
        <h2 class="text-xl font-bold">{{ patient.name }}</h2>
      </div>
      <div class="space-y-4">
        <div class="flex gap-3 items-center">
            <img src="../assets/calendarIcon.jpg" alt="calendarIcon">
          <div>
            <p class="text-sm text-gray-500">Date Of Birth</p>
            <p class="font-bold">{{ patient.date_of_birth }}</p>
          </div>
        </div>
        <div class="flex gap-3 items-center">
        <img src="../assets/FemaleIcon.svg" alt="femaleIcon">
          <div>
            <p class="text-sm text-gray-500">Gender</p>
            <p class="font-bold">{{ patient.gender }}</p>
          </div>
        </div>
        <div class="flex gap-3 items-center">
        <img src="../assets/PhoneIcon.svg" alt="PhoneIcon">
          <div>
            <p class="text-sm text-gray-500">Contact Info.</p>
            <p class="font-bold">{{ patient.phone_number }}</p>
          </div>
        </div>
        <div class="flex gap-3 items-center">
        <img src="../assets/PhoneIcon.svg" alt="PhoneIcon">
          <div>
            <p class="text-sm text-gray-500">Emergency Contacts</p>
            <p class="font-bold">{{ patient.emergency_contact }}</p>
          </div>
        </div>
        <div class="flex gap-3 items-center">
        <img src="../assets/insuranceIcon.svg" alt="insuranceIcon">
          <div>
            <p class="text-sm text-gray-500">Insurance Provider</p>
            <p class="font-bold">{{ patient.insurance_type }}</p>
          </div>
        </div>
      </div>
      <div class="mt-7 flex items-center justify-center">
        <button class=" bg-teal-400 rounded-full text-black font-bold py-2 px-4">
            Show All Information
        </button>
      </div>
    </div>
</template>
  
<script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    patient: {
      type: Object,
      required: true,
    },
  });
</script> 