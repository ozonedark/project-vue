<template>
  <form @submit="addItem">
      <input type="text" placeholder="Việc mới ..." v-model="title" >
      <input type="submit" value="Thêm" class="add-btn">
  </form>

</template>

<script>

import {v4 as uuidv4} from 'uuid'

export default {
  name: 'AddTodo',
  data() {
    return {
      title : ''
    }
  },
  methods: {
    addItem(event){
      event.preventDefault();
      const newItem = {
        id : uuidv4(),
        title : this.title,
        completed: false
      }
      this.$emit('add-todo', newItem)
      this.title = ''
    }
  }
}
</script>

<style scoped>
form {
 display: flex; 
}
input[type='text'] {
  flex: 10;
  padding: 5px;
}
input[type='submit'] {
  flex: 2;
}
</style>