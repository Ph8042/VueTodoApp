<template>
    <div>
      <div class="item">
        <p>New todo: {{ newItem }}</p>
        <input type="text" placeholder="todo" v-model="newItem">
        <button @click="addItem">add</button>
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
          { title: 'Do shopping', completed: false, id: '1' },
          { title: 'Do homework', completed: true, id: '2' }
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
      border: 1px solid #cdcdcd;
      margin: 8px;
      padding: 10px;
      border-radius: 15px;
    }
  
    .completed {
      opacity: 0.5;
    }
  
    .completed h2 {
      text-decoration: line-through;
    }
  </style>