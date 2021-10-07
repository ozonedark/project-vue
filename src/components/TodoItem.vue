<template>
    <li :class="['todo-item',todoProps.completed ? 'is-completed' : '']">
        <input type="checkbox" :checked="todoProps.completed" @change="markItemCompleted" />
        {{ todoProps.title }}
        <button class="del-btn" @click="deleteItem"> Delete</button>
    </li>
</template>

<script>


export default {
    name: 'TodoItem',
    props: ['todoProps'],
    data(props) {
        const markItemCompleted = () => {
            //console.log(props.todoProps.id)
            this.$emit('item-completed',props.todoProps.id)
        }  
        const deleteItem = () => {
            this.$emit('delete-item',props.todoProps.id)
        }  
        return{
            markItemCompleted,
            deleteItem
        }    
    }
  
}
</script>

<style>
.todo-item {
    background: #f4f4f4;
    padding: 10px;
    margin: 0;
    border-bottom: 1px #ccc dotted;
}
.del-btn {
    background: #ff0000;
    color: #fff;
    border: none;
    cursor: pointer;
    float: right;
}
.is-completed {
    text-decoration: line-through;
}
</style>