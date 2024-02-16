<template>
    <div class="btn-group">
        <button v-for="btn in filterButton" :key="btn.name" class="btn"
            :class="[filterNmae === btn.name ? 'btn-dark' : 'btn btn-outline-dark']" @click="filterHendler(btn.name)">
            {{ btn.title }}
        </button>
    </div>
</template>
<script>
export default {
    props: {
        updateFilter: {
            type: Function,
            required: true,
        },
        filterNmae: {
            type: String,
            required: true,
        },
    },
    data() {
        return {
            filterButton: [
                {
                    title: "Barcha Kinolar",
                    name: 'all'
                },
                {
                    title: "Mashhur Kinolar",
                    name: 'popular'
                },
                {
                    title: "Eng kop korilgan kinolar",
                    name: 'mostViewers'
                },
            ],
            filters: "all",
        };
    },
    methods: {
        filterHendler(fillter) {
            this.filter = fillter;
            this.updateFilter(this.filter);
        },
    },
};
</script>
<style></style>
