<template>
    <nav class="flex items-center justify-between px-4 py-2 bg-white rounded-full text-[#072635] font-bold text-sm">
      <!-- Logo Section -->
      <div class="pl-4">
        <img src="../assets/TestLogo.jpg" alt="Tech Care Logo" class="h-12">
      </div>
  
      <!-- Navigation Links -->
      <ul class="flex items-center space-x-4">
        <li>
          <a href="#" class="flex items-center space-x-2">
            <img src="../assets/homeIcon.svg" alt="HomeIcon">
            <span>Overview</span>
          </a>
        </li>
        <li>
          <a href="#" class="flex items-center space-x-2 bg-teal-400 px-3 py-2 rounded-full">
            <img src="../assets/patientIcon.svg" alt="Patient Icon">
            <span>Patients</span>
          </a>
        </li>
        <li>
          <a href="#" class="flex items-center space-x-2">
            <img src="../assets/sheduleIcon.svg" alt="Shedule Icon">
            <span>Schedule</span>
          </a>
        </li>
        <li>
          <a href="#" class="flex items-center space-x-2">
            <img src="../assets/chatIcon.svg" alt="Chat Icon">
            <span>Message</span>
          </a>
        </li>
        <li>
          <a href="#" class="flex items-center space-x-2">
            <img src="../assets/creditCardIcon.svg" alt="CreditCard Icon">
            <span>Transactions</span>
          </a>
        </li>
      </ul>
  
      <!-- User Profile Section -->
      <div class="flex items-center space-x-2">
        <img src="../assets/userProfileImg.png" alt="User Profile" class="h-11 w-11 rounded-full">
        <div class="text-left border-r pr-3">
          <p class="">Dr. Jose Simmons</p>
          <p class="text-[#707070]">General Practitioner</p>
        </div>
        <div class="flex gap-3 pr-3 pl-1">
          <img src="../assets/settingsIcon.svg" alt="Settings Icon">
          <img src="../assets/moreIcon.svg" alt="More Icon">
        </div>
      </div>
    </nav>
  </template>
  
  <script>
  export default {
    name: 'NavBar',
  };
  </script>