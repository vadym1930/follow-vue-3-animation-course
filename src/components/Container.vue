<template>
  <div class="container">
    <!-- <transition name="n" appear>
      <w-notification
        v-show="showNotification"
        warning
        bottom="true"
        round
        shadow
        transition="scale"
      >
        please enter a value
      </w-notification>
    </transition> -->
        <transition name="b" appear>
          <form @submit.prevent="Create()">
            <label>New item </label>
            <input
              type="text"
              v-model="msg"
              autocomplete="off"
            >
                <button>Add item</button>
          </form>
        </transition>
        <TodoList
          :TodoLists="TodoLists"
          :Delete="Delete"
        />
        <w-transition-bounce left>
          <w-card v-if="showNotification">
            pleade fill up the field
          </w-card>
        </w-transition-bounce>
  </div>
</template>

<script>
import TodoList from './TodoList';
import { ref } from "@vue/runtime-core";

export default {
  components: {
    TodoList,
  },
  data() {
    return {
      msg: '',
      showNotification: false,
      timeout: 2000
    }
  },
  setup() {
    let exampleData = [
      { id: 1, name: 'Item 1' },
      { id: 2, name: 'Item 2' },
      { id: 3, name: 'Item 3' },
    ];
    return {
      TodoLists: ref(exampleData)
    };
  },
  methods: {
    Create() {
      setTimeout(() => {
        this.showNotification = false;
      }, this.timeout);

      if (this.msg.length) {
        let id = Math.floor(Math.random() * 100);
        const next = { id, name: this.msg };
        this.TodoLists.push(next);
      } else {
        this.showNotification = true;
      }
    },
    Delete(idx) {
      this.TodoLists = this.TodoLists.filter((r) => r.id !== idx);
    }
  }
}

</script>

<style scoped>
  .b-enter-from {
    opacity: 0;
    transform: translateX(10px);
  }
/*
  .b-enter-to {
    opacity: 1;
    transform: translateX(0);
  } */

  .b-enter-active {
    transition: all 0.5s ease-in;
  }


  /* .b-leave-from {
    opacity: 1;
    transform: translateX(0);
  } */

  .b-leave-to {
    opacity: 0;
    transform: translateX(10px);
  }

  .b-leave-active {
    transition: all 0.5s ease-out;
  }

  .swop-enter-from, .swop-leave-to {
    opacity: 0;
    transform: translateX(40px);
  }

  /* .n-enter-active {
    animation: shake 0.95s ease-in;
  }

  @keyframes shake {
    0% {
      opacity: 0;
      transform: translateX(40px)
    }
    25% {
      opacity: 1;
      transform: translateX(-40px);
    }
    50% {
      transform: translateY(15px)
    }
    75% {
      transform: translateY(-15px)

    }
    100% {
      transform: translate(0);
    }
  } */
</style>
