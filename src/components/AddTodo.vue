<template>
  <div class="container">
    <div class="row d-flex justify-content-center">
      <div class="col-6">
        <div class="row">
          <div class="col-8">
            <b-form-input
              v-model="todoText"
              placeholder="I want to do ..."
            ></b-form-input>
          </div>
          <div class="col-4">
            <b-button variant="success" @click="addTodo">Add</b-button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todoText: "",
    };
  },
  methods: {
    addTodo() {
      this.$emit('addTodo', this.todoText);
      this.todoText = "";
    },
  },
};
</script>

<style>
</style>