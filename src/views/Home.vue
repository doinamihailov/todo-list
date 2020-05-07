<template>
  <div class="home">
    <img src="../assets/todo.png" alt=""
      contain
      height="100px"
      width="120px"
    >
    <HelloWorld msg="To do list" />
    <ToDo msg="TO DO list" :listTD=listTD />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import ToDo from '@/components/ToDo.vue'
export default {
  name: 'home',
  components: {
    HelloWorld,
    ToDo
  },
  data (){
      return {
        listTD: [
          { item: 1, name: 'Laundry', edit: false },
          { item: 2, name: 'Groceries', edit: false },
          { item: 3, name: 'Homework', edit: false },
          { item: 4, name: 'Call mom', edit: false }
        ]
      }
  },
  mounted() {
    if (localStorage.TD) {
      this.listTD = JSON.parse(localStorage.TD);
      //console.log("start baby" + JSON.parse(localStorage.TD))
    }
  },
    watch: {
      listTD(newTD) {
        localStorage.TD = JSON.stringify(newTD);
         //alert(JSON.stringify(newTD));

      }
    }
  }
</script>
