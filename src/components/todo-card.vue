<template>
  <div class="todo-card">
    <div class="todo-card-wrapper">
      <input
        @focus="todofocus = true"
        id="myInput"
        class="todo-card-input"
        placeholder="What is the plan?"
        type="text"
        v-model="todo"
        :class="{ todofocused: todofocus }"
        @blur="todofocus = false"
      />
      <button class="todo-card-clear" @click="this.todo = ''" v-if="this.todoLen" ><i class="fas fa-times"></i>
      </button>
      <input class="todo-card-submit" type="submit" value="Add" @click="addtodo" :class="{ disabledbtn: !todoLen , submitfocused: todofocus }" 
      />
    </div>
<ul>
    <span v-if="this.todos.length == 0">Nothing to do...</span>
     <li v-for="showtodo in todos" :key="showtodo"> <span class="text">{{showtodo.text}}</span>  {{showtodo.time}} 
      <button class="delete" @click="removeTodo(showtodo)"> 
       <i class="far fa-trash-alt"></i>   </button></li>

</ul>
     
  </div>
</template>

<script>



export default {
methods: {
  clickconsole () {
    console.log("clicked")
  },

  addtodo() {
      if(this.todoLen) {
             this.todos.push({
            
              text: this.todo,
              time: '',
              completed: false,
            });
            this.todo = '';
      }
   
              return;

      
    
  },

   removeTodo(showtodo) {
            this.todos.splice(this.todos.indexOf(showtodo), 1);
          },


} ,



computed: {
todoLen() {
    return  this.todo.length >= 1;
}
},

  data() {
    return {
      todo: '',
      todofocus: false,
      todos:[ ],

    };
  },
};
</script>

<style lang="scss" >

$yellow: rgb(255, 255, 141);
$dark: rgb(58, 58, 58);
$gray-1: rgb(220, 220, 220) ;
$gray-2: rgb(200, 200, 200) ;



.todo-card {
  width: 400px;
  max-width: 95%;
  background-color: white;
  border-radius: 5px;
  box-shadow: 0 0 3px 0px rgba(1, 1, 1, 0.1);
  display: flex;
  flex-direction: column;
  padding: 25px 25px;
  min-height: 70vh;
  border: 1px rgb(223, 221, 221) solid;
}

.todo-card-wrapper {
  display: flex;
  width: 100%;
  height: 30px;
    position:relative;

  .todo-card-input {
    display: flex;
    width: 80%;
    padding: 5px 8px;
    max-height: 30px;
    border-radius: 5px 0px 0px 5px;
    outline: none !important;
    border: $gray-1  2px solid;
    border-right: none !important;
  }

  .todo-card-clear {
    display: flex;
    width: 10%;
   height: 30px;
    outline: none !important;
      border: transparent 2px solid;
      border-left:none;
      border-right:none;
    background-color: transparent;
    align-items: center;
    justify-content: center;
    position:absolute;
    right:20%;
    color:$dark;
    font-weight: bold;
    cursor: pointer;
  }

  .todo-card-submit {
    width: 20%;
    padding: 5px 5px;
    max-height: 30px;
    border-radius: 0 5px 5px 0px;
    outline: none !important;
    border: $yellow  2px solid;

    cursor: pointer;
    border-left: none;
    font-weight: bold;
    background-color: $yellow;
    color: $dark;
  }

  .todofocused {
    background-color:rgba(255, 255, 208, 0.3) !important;
    border: $yellow 2px solid;
  }

  .submitfocused {
          border:  $yellow  2px solid !important;
            border-left:none !important;
  }

  .disabledbtn {
    user-select: none !important;
    background-color:$gray-1 !important;
    cursor:	auto !important;
    border: $gray-1  2px solid   ;
       border-left:none ;
       color:rgb(148, 148, 148) ;
    }
}

ul{
    padding:0;
    list-style-type: none;

    li{
        border:$gray-1 2px solid;
        border-radius: 15px;
        margin:2px 0;
        display:flex;
        padding:5px 10px;
        overflow:hidden;
        align-items: center;
.text {
    width:80%;
    overflow:hidden
}

        .delete {
    margin-left:auto;
    border-radius:50%;
    width:25px;
    height:25px;
    display:flex;
    justify-content: center;
    align-items: center;
    border:$gray-2 1px solid;
    background-color:$gray-1;
    color:$dark;
    cursor:pointer;
}

.delete:hover {
    background-color:$gray-2;
}

    }
}


</style>