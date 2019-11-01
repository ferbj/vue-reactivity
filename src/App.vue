<template>
  <div id="app">
    <div class="container">
      <Header />
      <AddItem v-on:add-item="addItem"/>
      <List v-bind:items="items"/>
    </div>
</div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import 'font-awesome/css/font-awesome.min.css'
import Header from './components/Header.vue'
import AddItem from './components/AddItem.vue'
import List from './components/List.vue'
export default {
  name: 'app',
  components: {
    Header,
    AddItem,
    List
  },
  data(){
    return {
      items:[
      {
        id:1,
        title: "One",
        completed: false,
      },
      {
        id:2,
        title: "Two",
        completed: true,
      },
      {
        id:3,
        title: "Three",
        completed: false,
      }
      ],
    }
   },
  methods: {
    addItem(newItem){
      this.items = [...this.items,newItem]
    }

  }
}

</script>

<style>
*{
  box-sizing: border-box;
  margin:0;
  padding:0;
}
body{
  font-family: Arial Helvetica sans-serif;
  line-height: 1.4;
}
</style>
