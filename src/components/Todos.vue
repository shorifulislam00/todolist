<template>
    <div>
        <div :key="todo.id" v-for="todo in todos">
            <TodoItem :todo="todo" @del-todo="$emit('del-todo', todo.id)" />
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
    name: "todos",
    components: {
        TodoItem
    },
    props: {
        todos: {
            type: Array,
            require: true
        }
    }
}
</script>

<style scoped>

</style>