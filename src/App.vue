<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo :allMoviesCount="movies.length" :favouritemovescounter="movies.filter(v => v.like).length" />
      <div class="search-panel">
        <SearchPanel :updateTerm="updateTerm" />
        <AppFilter :updateFilter="updateFilter" :filterNmae="filter" />
      </div>
      <MovieList @deleteItme="deleteItme" @onToogle="onToogle"
        :movies="onFillterHender(onSerarchc(movies, term), filter)" />
      <MovieAddForm @createMovie="createMovie" />
    </div>
  </div>
</template>

<script>
import AppInfo from "./components/app-info/AppInfo.vue";
import SearchPanel from "./components/search-panel/searchPanel.vue";
import MovieList from "./components/movie-list/MovieList.vue";
import AppFilter from "./components/app-filter/AppFilter.vue";
import MovieAddForm from "./components/movie-add-form/MovieAddForm.vue";

export default {
  components: {
    AppInfo,
    SearchPanel,
    MovieList,
    AppFilter,
    MovieAddForm,
  },
  data() {
    return {
      movies: [
        {
          id: 1,
          name: "Omar",
          viewers: 811,
          favourite: false,
          like: true,
        },
        {
          id: 2,
          name: "Empire of osman",
          viewers: 711,
          favourite: false,
          like: false,
        },
        {
          id: 3,
          name: "nimadur",
          viewers: 911,
          favourite: true,
          like: true,
        },
      ],
      term: '',
      filter: 'all',
    };
  },
  methods: {
    createMovie(itme) {
      this.movies.push(itme)
    },
    onToogle({ id, prop }) {
      this.movies = this.movies.map(v => v.id === id ? { ...v, [prop]: !v[prop] } : v)
    },
    deleteItme(id) {
      this.movies = this.movies.filter(v => v.id !== id)
    },
    onSerarchc(arr, term) {
      if (term.length == 0) {
        return arr
      }
      else {
        return arr.filter(v => v.name.toLowerCase().indexOf(term) > -1)

      }
    },
    onFillterHender(arr, filter) {
      switch (filter) {
        case "popular":
          return arr.filter(v => v.like);
        case "mostViewers":
          return arr.filter(v => v.viewers > 500)
        default:
          return arr
      }
    },

    updateTerm(value) {
      this.term = value
    },
    updateFilter(filter) {
      this.filter = filter

    }
  },
};
</script>

<style>
.app {
  height: 100vh;
  color: #000;
}

.content {
  width: 1000px;
  min-height: 700px;
  background-color: #fff;
  margin: 0 auto;
  padding: 5rem 0;
}

.search-panel {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 5px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.5);
}
</style>
