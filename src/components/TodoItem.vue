<template>
    <div class="todo-item">
        <p v-bind:class="{'is-complete':todo.completed}">
            <input type="checkbox" v-on:change="markComplete">
            <button v-on:click="$emit('del-todo', todo.id)" class="del"> X </button>
             {{todo.title}} </p>
        
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed= !this.todo.completed;
        }
    }
}
</script>

<style scoped>
.todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
}

.is-complete {
    text-decoration: line-through;
}

.del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right; 
}

</style>
