<template>
  <transition name="swop" mode="out-in">
    <div v-if="TodoLists.length > 0">
      <transition-group tag="ul" name="todo">
        <li v-for="(todolist, index) in TodoLists" :key="index">
          <span class="name">{{todolist.name}}</span>
          <button @click="Delete(todolist.id)">X</button>
        </li>
      </transition-group>
    </div>
    <div v-else>
      <p>No items</p>
    </div>
  </transition>
</template>

<script>

export default {
  props: {
    TodoLists: Array,
    Delete: Function
  },
}
</script>

<style scope>
  .todo-enter-from {
    opacity: 0;
    transform: scaleY(0.25);
  }
  .todo-enter-to {
    opacity: 1;
    transform: scaleY(1);
  }
  .todo-enter-active {
    transition: all .5s ease-in;
  }
  .todo-leave-from {
    opacity: 1;
    transform: scaleY(1);
  }
  .todo-leave-to {
    opacity: 0;
    transform: scaleY(0.25);
  }
  .todo-leave-active {
    transition: all .5s ease-out;
  }
  .swop-enter-active, .swop-leave-active {
    transition: all, .5s ease;
  }
  .swop-leave-from, .swop-enter-to {
    opacity: 1;
    transform: translateX(0);
  }
</style>
