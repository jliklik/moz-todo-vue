<template>
    <div>
        <input type="checkbox" :id="id" :checked="isDone" />
        <label for="todo-item">{{ label }}</label>
    </div>
</template>


<script>
export default {
    // props are objects that hold state (properties)
    props: {
        label: {required: true, type: String}, // can bind to labels
        done: {default: false, type: Boolean},
        id: { required: true, type: String }
    },
    // data is used to maintain state
    data() {
        return {
            isDone: this.done, // use v-bind:<property>=<data_key> or :<property>=<data_key> to bind a property to data
        }
    }
};
</script>