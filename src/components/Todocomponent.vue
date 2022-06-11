<template>
  <div class="container bg-white max-w-xs mx-auto rounded-sm my-24">
    <h2 class="font__roborto my-2 p-2 text-center">
      We keep your TODO<sub>s</sub> alive
    </h2>
    <span class="px-8 text-blue font-bold"
      >{{}}
      <span class="font-light"> {{ new Date().toLocaleString() }}</span></span
    >
    <form @submit.prevent="addTodo" class="form text-center my-2 p-2">
      <input
        class="add__input bg-wheat outline-4 outline-offset-8 outline outline-blue p-2 text-app-blue"
        type="text"
        name="Add Todo"
        placeholder="Add your next TODO..!"
        v-model="title"
      />
      <button class="mx-2 bg-blue px-5 rounded-sm py-1 text-xl text-white">
        +
      </button>
    </form>
    <div class="flex justify-center py-2">
      <button
        class="text-center mx-2 bg-wheat p-1 text-app-blue font__roborto font-bold button"
      >
        Click the TODO to complete
      </button>
      <button
        @click="$emit('remove', i)"
        class="justify-center bg-wheat p-1 text-app-blue font__roborto font-bold outline-0 button"
      >
        clear all
      </button>
    </div>
    <slot />
  </div>
</template>

<script>
export default {
  name: "todo-component",
  //props: ["todos"],
  data() {
    return {
      title: null,
    };
  },
  methods: {
    addTodo() {
      if (!this.title) return;

      this.$emit("add", { title: this.title });
      this.title = null;
    },
  },
};
</script>

<style scoped lang="postcss"></style>
