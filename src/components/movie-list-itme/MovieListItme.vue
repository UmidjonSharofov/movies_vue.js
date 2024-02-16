<template>
    <li class="list-group-itme d-flex justify-content-between"
        :class="[{ like: movies.like }, { favourite: movies.favourite }]">
        <span @click="$emit('onToogle', { id: movies.id, prop: 'like' })" class="list-group-itme-label">{{ movies?.name
        }}</span>
        <input type="number" class="list-group-itme-input" :value="movies.viewers" />
        <div class="d-flex justify-content-center aligen-items-center">
            <div class="btnDlelete">
                <BgColorsOutlined @click="$emit('onToogle', { id: movies.id, prop: 'favourite' })" class="iconsStar" />
            </div>
            <div class="btnDlelete">
                <DeleteOutlined @click="deleteItme" class="iconsdelete" />
            </div>
            <div class="btnDlelete none">
                <StarOutlined class="fa-star" />
            </div>
        </div>
    </li>
</template>
<script>
import { DeleteOutlined, StarOutlined, BgColorsOutlined } from "@ant-design/icons-vue";
export default {
    props: {
        movies: {
            type: Object,
            required: true,
        },
    },
    components: {
        DeleteOutlined,
        StarOutlined,
        BgColorsOutlined,
    },
    methods: {
        deleteItme() {
            this.$emit('deleteItme', this.movies.id)
        }
    }
};
</script>
<style scoped>
.list-group-itme {
    padding: 15px 20px;
    border-bottom: 1px solid #3d5a80;
}

.list-group-itme:last-child {
    border-bottom: none;
}

.list-group-itme span {
    line-height: 35px;
    font-size: 20px;
    cursor: pointer;
    width: 550px;
}

.list-group-itme input {
    line-height: 35px;
    font-size: 20px;
    text-align: center;
    border: none;
    outline: none;

}

.btnDlelete {
    max-width: 35px;
    max-height: 35px;
    margin: 3px;
    display: flex;
    font-size: 17px;
    align-content: center;
    justify-content: center;
    background: #e2e2e2;
    cursor: pointer;
}

.iconsdelete {
    color: #e5383b;
}

.iconsStar {
    color: #e09f3e;
}

.none {
    background-color: #fff;
}

.fa-star {
    background: none;
    max-height: 35px;
    max-width: 35px;
    color: #ffd700;
    transition: 0.3s all;
    transform: translateX(30px);
    opacity: 0;
}

.list-group-itme.like .fa-star {
    opacity: 1;
    transform: translate(0px);
}

.list-group-itme.favourite .list-group-itme-label {
    color: #e09f3e;
}

.list-group-itme.favourite .list-group-itme-input {
    color: #e09f3e;
}
</style>
