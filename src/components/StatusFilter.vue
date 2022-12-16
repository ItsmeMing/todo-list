<script setup>
import {inject} from "vue";

defineEmits(["checked"]);
const todosStatus = inject("todosStatus");
</script>

<template>
    <div class="todos__filter">
        <div class="filter__heading">
            <FontAwesomeIcon icon="fa-solid fa-filter" />
            <h1>Filter:</h1>
        </div>
        <div
            class="filter__item"
            v-for="(status, key) in todosStatus"
            :key="key"
        >
            <input
                :id="status.name.toLowerCase().replace(/\s/g, '')"
                type="checkbox"
                :v-model="status.checked"
                @click="$emit('statusChecked', status.name, $event)"
                :checked="status.checked"
            />
            <label :for="status.name.toLowerCase().replace(/\s/g, '')">{{
                status.name
            }}</label>
        </div>
    </div>
</template>

<style scoped lang="scss">
.todos__filter {
    display: flex;
    gap: 15px;
    margin-bottom: 20px;
    .filter__heading,
    .filter__item {
        display: flex;
        gap: 5px;
        font-size: 20px;
        h1 {
            font-weight: 600;
        }
    }
}
</style>
