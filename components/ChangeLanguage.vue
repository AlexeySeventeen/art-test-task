<template>
    <div>
      <select class="outline-0" v-model="selected" @change.stop="$emit('change', selected)">
        <option value="ru">Русский</option>
        <option value="en">English</option>
      </select>
    </div>
  </template>
  
  <script setup>
  const selected = ref('ru');
  </script>
  