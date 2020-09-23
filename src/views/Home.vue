<template>
  <div class="home">
  <todo-card></todo-card>
  </div>
</template>

<script>
import todoCard from "../components/todo-card.vue";

export default {
components:{
  todoCard
}
}
</script>

<style lang="scss">
.home {
  display:flex;
  justify-content: center;
  align-items: center;
  padding:5% 5%
}
</style>