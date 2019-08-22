Skip to content
 
Search or jump to…

Pull requests
Issues
Marketplace
Explore
 
@shoppertest 
Learn Git and GitHub without any code!
Using the Hello World guide, you’ll start a branch, write comments, and open a pull request.

 
6
128 61 bradtraversy/vue_crash_todolist
 Code  Issues 1  Pull requests 0  Projects 0  Wiki  Security  Insights
vue_crash_todolist/src/components/AddTodo.vue
@lusarz lusarz Refactor form submit prevent default
3806a93 on Jan 13
@bradtraversy @lusarz
50 lines (42 sloc)  737 Bytes
    
<template>
  <div>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
import uuid from 'uuid';
export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo() {
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      }
      // Send up to parent
      this.$emit('add-todo', newTodo);
      this.title = '';
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>



