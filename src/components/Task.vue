<template>
  <div class="task" :class="stateClass">
    <v-checkbox
      v-model="checkbox"
      @click="$emit('taskStateChanged', task)"
    ></v-checkbox>
    <v-icon @click.stop="$emit('taskDeleted', task)" class="close">{{
      svgDelete
    }}</v-icon>
    <v-text>{{ task.name }}</v-text>
  </div>
</template>

<script>
import { mdiTrashCanOutline } from "@mdi/js";

export default {
  props: {
    task: { type: Object, required: true },
  },
  data() {
    return {
      svgDelete: mdiTrashCanOutline,
      checkbox: !this.task.pending,
    };
  },
  computed: {
    stateClass() {
      return {
        pending: this.task.pending,
        done: !this.task.pending,
      };
    },
  },
};
</script>

<style>
.task {
  position: relative;
  box-sizing: border-box;
  width: 600px;
  height: 70px;
  padding: 20px;
  border-radius: 10px;
  font-size: 1.2rem;
  font-weight: 500;
  cursor: pointer;
  user-select: none;
  display: flex;
  align-items: center;
  background-color: rgba(128, 128, 128, 0.349);
}

.pending {
}

.done v-text {
  color: #ddd;
  text-decoration: line-through;
}
.done {
  background-color: rgba(128, 128, 128, 0.041);
}

.close {
  position: absolute;
  left: 500px;
  top: 0px;
  font-size: 0.9rem;
  font-weight: 600;
  height: 40px;
  width: 40px;
  border-radius: 10px;
  display: flex;
  justify-content: end;
}
.close:hover {
  background-color: rgba(39, 38, 38, 0.253);
}
</style>