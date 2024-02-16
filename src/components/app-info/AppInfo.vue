<template>
  <div class="app-info">
    <p class="fs-3 tetx-uppercase">Barcha kinolar soni: {{ allMoviesCount }}</p>
    <p class="fs-4 text-uppercase">kinolar soni: {{ favouritemovescounter }}</p>
  </div>
</template>

<script>
export default {
  props: {
    allMoviesCount: {
      type: Number,
      required: true,
    },
    favouritemovescounter: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style scoped>
.app-info {
  padding: 1.5rem;
  border-radius: 4px;
  background-color: #fafaf5;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>
