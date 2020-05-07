<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <a>Before Monday</a>
      <table class="center">
          <tr v-for="el in list2" v-bind:key="el">
               <td>
                    <span v-show="!el.edit">{{el.name}}</span>
                    <input type="text" v-model="el.name" v-show="el.edit" >
               </td>
               <td>
                    <button v-on:click="removeElement(el)">x</button>
               </td>
               <td>
                    <button v-show="!el.edit" v-on:click="editElement(el)">edit</button>
                    <button v-show="el.edit" v-on:click="viewElement(el)">save</button>
               </td>
          </tr>
            <div class="add">
                 <input type="text" v-model="value">
                <button v-on:click="addV()">add</button>
            </div>
     </table>
  </div>
</template>

<script>

export default {
  name: 'ToDo',
  props: {
    msg: String,
    listTD: Array
  },
  data (){
      return {
          add: false,
          value: "",
      }
  },
  computed:{
          list2: function(){
               var l = [];
               console.log(this.listTD)
               for (var i = 0, lis; lis= this.listTD[i]; i++){
                    lis.edit = false;
                    l.push(lis);
               }
               return l;
          }
     },
  methods: {
    removeElement: function (el) {
      const index = this.listTD.indexOf(el)
      this.listTD.splice(index, 1)
    },
    editElement: function(el){
        el.edit = true;
    },
    viewElement: function(el){
        el.edit = false;
    },
    addV: function() {
        this.listTD.push({
            item: this.listTD[this.listTD.length - 1].item + 1,
            name: this.value,
            edit: false
            });
        this.value = ""
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul{
  list-style-type: none;
  padding: 0;
  display: block;
}
li{
  display: block;
  margin: 0 10px;
  width: 100%;
}
a {
  color: #42b983;
}
button {
    margin-left:20px;
}
table.center {
    margin-left:auto; 
    margin-right:auto;
  }
  .add {
    margin-left:120px; 
    margin-right:auto;
  }
</style>
