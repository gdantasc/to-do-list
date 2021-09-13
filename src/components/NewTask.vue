<template>
  <div class="new-task">
    <div class="form">
      <input
        v-model="name"
        @keydown.enter="add"
        type="text"
        class="form-element"
        placeholder="Nova Tarefa ?"
      />
      <v-btn @click="add" class="form-btn">Create</v-btn>
         </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      name: "",
      
    };
  },
  methods: {
    add() {
      this.$emit("taskAdded", { name: this.name });
      this.name = "";
    },
  },
};
</script>

<style>
.new-task {
  margin: 35px;
}

.form-element {
  position: relative;
  color: #fff;
  width: 100%;
  height: 100%;
  padding: 10px;
}

.form-btn {
  position: absolute;
   
}

.form {
  margin: auto;
  justify-content: center;
  background-color: rgba(128, 128, 128, 0.349);
  border-radius: 10px;
  width: 450px;
  height: 60px;
}
</style>