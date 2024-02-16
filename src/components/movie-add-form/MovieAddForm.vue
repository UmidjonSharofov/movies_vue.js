<template>
  <div class="movie-app-form">
    <h3>Yangi kino qo'shish</h3>
    <form action="" class="add-form d-flex" @submit.prevent>
      <input type="text" class="form-control new-movie-label" placeholder="Qanday kinop" :value="name"
        @input="name = $event.target.value" />
      <input type="number" class="form-control new-movie-label" placeholder="Neca marotaba ko'rilgan?" :value="viewers"
        @input="viewers = $event.target.value" />
      <button class="btn btn-outline-dark" @click="addMovie" type="submit">
        Qo'shish
      </button>
    </form>
  </div>
</template>
{}
<script>
export default {
  data() {
    return {
      name: "",
      viewers: "",
    };
  },
  methods: {
    addMovie() {
      if (this.name && this.viewers) {
        const newMovie = {
          name: this.name,
          viewers: this.viewers,
          favourite: false,
          like: false,
          id: Date.now(),
        };
        this.$emit("createMovie", newMovie);
        this.name = ""
        this.viewers = ""
      }
    },
  },
};
</script>
<style>
.movi-app-form {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 5px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.5);
}
</style>
