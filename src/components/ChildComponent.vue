<template>
    <div>
      <h2>Child Component</h2>
      <div>
        <label for="userId"><strong>User ID:</strong></label>
        <input type="text" :value="userId" @input="$emit('userId')" />
      </div>
      <div>
        <label for="title"><strong>Title:</strong></label>
        <input type="text" :value="title" @input="$emit('title')" />
      </div>
      <div>
        <label for="completed"><strong>Completed:</strong></label>
        <input type="text" :value="completed.toString()" />
      </div>
    </div>
  </template>
  
  <script setup>
  
  defineProps(['userId', 'title', 'completed']);
  </script>
  
  <style scoped>
  
  </style>
  