<template >
    <div class="serch-panel">
        <input class="form-control search-input" @input="changeHender" :value="term" type="text"
            placeholder="Kinolarni qidirish ">
    </div>
</template>
<script>
export default {
    props: {
        updateTerm: {
            type: Function,
            required: true
        }
    },
    data() {
        return {
            term: ''
        }
    },
    methods: {
        changeHender(e) {
            this.term = e.target.value
            this.updateTerm(this.term)
        }
    }
}
</script>
<style >
.search-input {
    margin-top: 2rem;
    margin-bottom: 1rem;
    padding: 1.5rem;
    background-color: #fcfaf5;
    border-radius: 5px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.5);
}
</style>