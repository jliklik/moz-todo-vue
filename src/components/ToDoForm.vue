<template>
  <form @submit.prevent="onSubmit">
    <h2 class="label-wrapper">
      <label for="new-todo-input"> 
        What needs to be done? 
      </label>
    </h2>
    <input
      type="text"
      id="new-todo-input"
      name="new-todo"
      autocomplete="off" 
      v-model.lazy.trim="label"
      class="input__lg"/>
    <button type="submit" class="btn btn__primary btn__lg">Add</button>
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
