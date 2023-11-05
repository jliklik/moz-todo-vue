<template>
  <form @submit.prevent="onSubmit">
    <label for="new-todo-input"> What needs to be done? </label>
    <input
      type="text"
      id="new-todo-input"
      name="new-todo"
      autocomplete="off" 
      v-model.lazy.trim="label"/>
    <button type="submit">Add</button>
  </form>
</template>

<script>
  export default {
    // callbacks
    methods: {
      // bind to callbacks using @ syntax. 
      // Use .prevent to prevent event's default behavior (eg. submit would refresh the page and get info from server)
      onSubmit() { 
        if (this.label === "") {
          return;
        }
        this.$emit("todo-added", this.label); // emit events so parent can make use of child updates
        this.label = ""; // reset input
      }
    },
    data() {
      return {
        label: ""
      }
    }
  };
</script>