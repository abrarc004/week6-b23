<template>
  <div id="app">
  <h1>Hello World</h1>
  <p>My name is {{name}}. I am {{age}} years old</p>
  <button v-on:click="sayHello">Press me!</button>
  <hr>
  <h2>Simple Counter</h2>
  <p>{{digit}}</p>
  <p>{{message}}</p>
  <button v-on:click="addClick">Increment</button>
  <button v-on:click="minusClick">Decrement</button>
  <button v-on:click="clearValue">Reset</button>
  <hr>
  <h2>Simple input</h2>
  <input type="text" name="name" placeholder="Enter your name" v-model="inputName">
  <button v-on:click="inputPressed">Click me!</button>
  <p>{{inputMessage}}</p>
  <hr>
  <h2>My to do list</h2>
  <input type="text" name="todoItem" v-model="todoItem">
  <button v-on:click="todoPressed">To Do pressed</button>
  <ul>
    <li v-for="item in items" :key="item">{{item}}</li>
  </ul>
  <hr>
  <h2>My Shopping Plan</h2>
  <input type="text" name="shoppingItem" v-model="shoppingItem">
  <input type="number" name="shoppingPrice" v-model="shoppingPrice">
  <button v-on:click="addItemPressed">Add new Item</button>
  <table>
    <thead>
      <tr>
        <th>Item</th>
        <th>Price</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in shoppingItems" :key="item.shoppingItem">
        <td>{{item.shoppingItem}}</td>
        <td>{{item.shoppingPrice}}</td>
        <td><button v-on:click="deleteItem(item)">Delete</button></td>
      </tr>
    </tbody>
  </table>

</div>  
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      name:"Abrar",
      age: 30,
      digit: 0,
      message: "",
      inputMessage: "",
      inputName: "",
      todoItem:"",
      items:[],
      todoItems:[],
      shoppingItem:"",
      shoppingPrice:"",
      shoppingItems:[]
    }
  },
  methods:{
    deleteItem:function(item){
      for(var i = 0; i < this.shoppingItems.length; i++){
        if(item.shoppingItem == this.shoppingItems[i].shoppingItem && item.shoppingPrice == this.shoppingItems[i].shoppingPrice){
          this.shoppingItems.splice(i,1);
        }
      }
    },
    addItemPressed:function(){
      this.shoppingItems.push({
        shoppingItem:this.shoppingItem,
        shoppingPrice:this.shoppingPrice
      })
      this.shoppingItem ="";
      this.shoppingPrice = "";
    },
    todoPressed:function(){
      this.items.push(this.todoItem);
      console.log(this.items);
      this.todoItem ="";
    },
    inputPressed:function(){
      this.inputMessage ="Hello "+this.inputName;
    },
    sayHello:function(){
      alert("Hello World");
    },
    minusClick:function(){
      if( this.digit > 0){
       this.digit--;
      }
      else {
        this.message = "Number cannot be less than 0";
      }
    },
    addClick:function(){
      this.digit++;
      this.message = "";
    },
    clearValue:function(){
      this.digit = 0;
      this.message = "";
    },
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
</style>
