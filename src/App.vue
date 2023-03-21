<template>
  <h1>{{ todo }}</h1>
  <div class="container">
        <div class="form">
            <input v-model.trim="todo" type="text" class="input" />
            <input @click="addTodo" type="submit" class="add" value="Add Task" />
        </div>
        
        <div 
        v-for="(item,idx) in todos"
        :key="idx" 
        class="tasks"
        style="display: flex; align-items:center; justify-content:space-between"
        >
        <span>{{ item.title }}</span>
        <button @click="deleteItem(item)" class="del">Delete</button>
        </div>
        <div @click="deleteAll" class="delete-all">Delete all</div>
        </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      title:"Todo APP",
      todo:'',
      todos:[
        {
          id:1,
          title:"salom"
        },
        {
          id:2,
          title:"hayr"
        }
      ]
    }
  },
  methods:{
    addTodo(){
      if(this.todo.trim()){
      this.todos.push({
        title:this.todo,
        id:Math.floor(Math.random()*1000)
      })
      this.todo =''
    }
    },
    deleteItem(idx){
      this.todos.splice(idx,1)
    },
    deleteAll(){
      this.todos =[]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
            font-family: Arial, Helvetica, sans-serif;
        }
        .container {
            width: 500px;
            margin: 20px auto;
        }
        .form {
            background-color: #eee;
            border-radius: 6px;
            padding: 20px;
            display: flex;
            align-items: center;
        }
        .input {
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 6px;
            flex: 1;
        }
        .input:focus , .add:focus{
            outline: none;
        }
        .add {
            border: none;
            background-color: #f44336;
            color: white;
            padding: 10px;
            border-radius: 6px;
            margin-left: 10px;
            cursor: pointer;
        }
        .tasks {
            background-color: #eee;
            margin-top: 20px;
            border-radius: 6px;
            padding: 20px;
        }
        .tasks .task {
            background-color: white;
            padding: 10px;
            border-radius: 6px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: 0.3s;
            cursor: pointer;
            border: 1px solid #ccc;
        }
        .tasks .task:not(:last-child) {
            margin-bottom: 15px;
        }
        .tasks .task:hover {
            background-color: #f7f7f7;
        }
        .tasks .task.done {
            opacity: 0.5;
            position: relative;
        }
        .task.done::after {
            position: absolute;
            content: "";
        }
        .tasks .task span { 
            font-weight: bold;
            font-size: 10px;
            background-color: red;
            color: white;
            padding: 2px 6px;
            border-radius: 4px;
            cursor: pointer;
        }
        .delete-all {
            width: calc(100% - 25px);
            margin: auto;
            padding: 12px;
            text-align: center;
            font-size: 14px;
            color: white;
            background-color: #f44336;
            margin-top: 20px;
            cursor: pointer;
            border-radius: 4px;
        }
        .del{
          background-color: #f44336;
          padding: 12px 20px;
            text-align: center;
            font-size: 14px;
            color: white;
            border: none;
            outline: none;
            border-radius: 10px; 
        }
</style>
