<template>
  <div>
        <ul>
      <span v-if="this.todos.length == 0">Nothing to do...</span>
      <li v-for="showtodo in todos" :key="showtodo">
        <span class="text">{{showtodo.text}}</span>

        {{showtodo.time}}
        <input
          placeholder="What is the plan?"
          type="text"
          v-model="updatetodo"
          @keyup.enter="updatedtodo(showtodo)"
        />
        <button class="delete" @click="removeTodo(showtodo)">
          <i class="far fa-trash-alt"></i>
        </button>
      </li>
     
    </ul>
  </div>
</template>

<script>

export default {


}
</script>

<style>

</style>