<template>
    
    <div class="todo-list"> 
        <AddTodo @add-todo="addTodo" />
        <ul>
            <TodoItem  v-for="todo in todos" 
            :key="todo.id" 
            :todoProps="todo"
            @item-completed="markComplete"
            @delete-item="deleteTodo"
            />
        </ul>
    </div>
   
</template>

<script>

import TodoItem from './TodoItem'
import AddTodo from './AddTodo'
import {v4 as uuidv4} from 'uuid'

export default {
    name: 'Todos',
    components: {TodoItem, AddTodo},
    data() {
        
        return {
            todos: [
                {id: uuidv4(), title:'Viec 1', completed: false},
                {id: uuidv4(), title:'Viec 2', completed: false},
                {id: uuidv4(), title:'Viec 3', completed: false}
            ],
         
        }
    },
    methods: {
        markComplete (id) {
            this.todos = this.todos.filter(x => {  
                if(x.id === id) 
                    x.completed = !x.completed
                return x
            })
        },
        deleteTodo(id){
            this.todos = this.todos.filter(x => {  
                if(x.id !== id) 
                return x
            })
        },
        addTodo(newTodo){
            this.todos.push(newTodo)
        }
    },
}
</script>

<style>
.todo-list ul {
    padding: 0 10px 10px 10px;
    list-style-type: none;
}

/* .todo-list li {
    padding: 10px;
    cursor: pointer;
    margin: 10px 0;
    border-radius: 4px;
    background: rgb(240,240,240);
    color: black;
} */
</style>