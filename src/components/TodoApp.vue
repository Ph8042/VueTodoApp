<template>
    <div>
      <div class="item">
        <p>New todo: {{ newItem }}</p>
        <input type="text" placeholder="ADD YOUR TASK" v-model="newItem">
        <button @click="addItem">ADD</button>
      </div>
      
      <TodoItem 
      v-for="item in items" 
      v-bind:key="item.id"
      v-bind:item="item" 
      @removeClicked="removeItem"
        />

    </div>
  </template>
  
  <script>
  import TodoItem from './TodoItem.vue'
  export default {
    components: {
        TodoItem
    },
    data() {
      return {
        newItem: '',
        items: [
         // { title: 'Do shopping', completed: false, id: '1' },
         // { title: 'Do homework', completed: true, id: '2' }
        ]
        }
      },
    methods: {
      addItem() {
        this.items.push({ 
          title: this.newItem, 
          completed: false, 
          id: Math.random() 
        })
        this.newItem = ''
      },
      removeItem(id) {
        const index = this.items.findIndex(el => el.id === id)
        this.items[index].completed = true
      },
    }
  }    
  
  
  
  </script>
  
  <style>
    .item {
      border: 1px dotted #c8c8c8;
      margin: 8px;
      padding: 10px;
      border-radius: 15px;
      display: flex;
      flex-direction: column;
      gap: 10px;
      flex-wrap: wrap;
      font-size: 17px;
      width: 500px;;
      align-items: center;
      justify-content: center;

    }
  
    .completed {
      opacity: 0.5;
    }
  
    .completed h2 {
      text-decoration: line-through;
    }

    body {
      letter-spacing: 0.1px;
      margin: 0;
      padding: 0;
      font-family: 'Share Tech Mono', Monospace, Courier;
      font-weight: 400;
      font-size: 17px;
      color: #c8c8c8;
      background: #222;
      display: flex;
      justify-content: center;
      align-content: center;
    }

    button {
      color: #c8c8c8;
      background: #222;
      border: 0.8px solid #c8c8c8;
      border-radius: 5px;
      width: 50px;
      align-items: center;
      justify-content: center;
      font-size: 12px;
      margin-bottom: 20px;
    }

    h1 {
      text-align: center;
    }

    h2 {
      font-size: 17px;
    }

    input {
      text-align: center;
      border: solid #00000 0.5px;
      border-radius: 8px;
      width: 50%;
      color: #000000;
      background: ;
      height: 25px;
      margin-bottom: 15px;
    }
  </style>