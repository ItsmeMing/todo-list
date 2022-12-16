<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
defineProps(["todo"]);
</script>

<template>
    <div class="todo" v-if="todo.showed">
        <div class="todo__heading">
            <h2>{{ todo.title }}</h2>
            <div :class="`priority ${todo.status.toLowerCase().replace(/\s/g, '')}`">{{ todo.priority }}</div>
        </div>
        <p class="todo__description">{{ todo.description }}</p>
    </div>
</template>

<style scoped lang="scss">
.todo {
    margin-bottom: 10px;
    padding: 10px 15px;
    background-color: var(--soft-brown);
    border-radius: 4px;
    .todo__heading {
        display: flex;
        font-size: 16px;
        margin-bottom: 10px;
        > * {
            padding: 5px 0;
        }
        h2 {
            color: rgb(var(--dark));
        }
        .priority {
            color: var(--soft-brown);
            padding-left: 5px;
            padding-right: 5px;
            margin-left: 10px;
            border-radius: 4px;
        }
    }
    .todo__description {
        font-size: 15px;
        word-wrap: break-word;
    }
}
</style>
