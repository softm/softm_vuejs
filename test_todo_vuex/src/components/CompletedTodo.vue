<template>
    <div>
        Completed Todo: {{ numberOfCompletedTodo }}
    </div>
</template>

<script>
export default {
    computed: {
        todos(){
            return this.$store.state.todos;
        },
        numberOfCompletedTodo() {
            // return this.$store.getters['todo/numberOfCompletedTodo'];
            return this.$store.getters.numberOfCompletedTodo;
            // return this.todos.filter(todo => todo.checked).length;
        }
    }
}
</script>

<style>
</style>