<script setup>
import CardClima from "./components/CardClima.vue";
</script>

<template>
  <div
    class="hero min-h-screen"
    style="
      background-image: url(https://img.freepik.com/free-vector/sky-background-video-conferencing_23-2148639325.jpg?size=626&ext=jpg&ga=GA1.1.735520172.1710979200&semt=ais);
    "
  >
    <div class="hero-overlay bg-opacity-20"></div>
    <div class="hero-content text-center text-neutral-content">
      <div >
        <h1 class="mb-5 font-bold">
          <CardClima />
        </h1>
      </div>
    </div>
  </div>
</template>

