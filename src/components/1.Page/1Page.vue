<!-- Datei: src/components/2.Page/2Page.vue -->

<template>
  <div class="page">
    <div class="wrapper">
      <div class="greetings">
        <h1>{{ msg }}</h1>
        <h3>Unserer neue Webseite befindet sich gerade im Aufbau.</h3>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
});
</script>

<style scoped>
.page {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  text-align: center;
}

.wrapper {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.greetings h1 {
  color: #6200EA; /* Beispiel einer Primärfarbe */
  margin-bottom: 20px;
}

.greetings h3 {
  color: #333;
  margin-bottom: 10px;
}
</style>
