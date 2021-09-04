<template>
  <div class="container">
    <div class="row d-flex justify-content-center">
      <div class="col-6">
        <table class="table">
          <tbody>
            <tr>
              <td v-if="editMode">
                <b-form-input v-model="todoText"></b-form-input>
              </td>
              <td v-else>{{ todo.text }}</td>

              <td>
                <b-button
                  variant="outline-info"
                  v-if="editMode"
                  @click="saveEdit"
                  >Save change</b-button
                >
                <b-button variant="warning" v-else @click="enableEdit"
                  >Edit</b-button
                >
              </td>
              <td>
                <b-button
                  variant="danger"
                  @click="$emit('deleteHandler', todo.key)"
                  >Delete</b-button
                >
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      editMode: false,
      todoText: "",
    };
  },
  emit: ["deleteHandler", "saveEdit"],
  props: {
    todo: {
      type: Object,
      require: true,
    },
  },
  methods: {
    enableEdit() {
      this.editMode = true;
      this.todoText = this.todo.text;
    },
    saveEdit() {
      this.$emit("saveEdit", { key: this.todo.key, text: this.todoText });
      this.editMode = false;
      this.todoText = "";
    },
  },
};
</script>

<style>
.table {
  margin-bottom: 0 !important;
}
</style>