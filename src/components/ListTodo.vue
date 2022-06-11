<template>
  <ul class="todo__ul p-3">
    <span class="font__roborto font-extrabold text-xl"
      >You have {{ this.todos.length }} Pending TODOs
    </span>
    <li
      v-for="(todo, i) in todos"
      :key="i"
      class="todo__item my-2 p-2 flex justify-between"
    >
      <div>
        <p @click="toggle" class="p-2">
          {{ todo }}
        </p>
      </div>
      <div @click="$emit('remove', i)" class="delete__button m-1 max__width">
        <button @click="$emit('remove', i)" class="delete__button"></button>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: "list-todo",
  props: ["todos"],
  data() {
    return {};
  },
  methods: {
    toggle(event) {
      event.target.classList.toggle("done__item");
    },
  },
};
</script>

<style scoped>
.done__item:before {
  content: "----------------------------------------";
  position: absolute;
  right: 43%;
}
.wrapping {
  white-space: nowrap;
}

.max__width {
  max-width: 2em;
}
</style>
