<template>
  <li>

  
    <button v-bind:class="className">
      <i @click="$emit('complete')"  class="far fa-circle"></i>{{ task.title }}
    </button>
    


    <th scope="col">{{ task.date }}</th>
    <button @click="$emit('remove')"><i class="far fa-trash-alt"></i></button>
 
  </li>
</template>

<script>
export default {
  name: "taskname",
  props: ["task"],

  computed: {
    className() {
      let classes = ["toggle"];
      if (this.task.completed) {
        classes.push("toggle-completed");
      }
      return classes;
    },
  },
};
</script>
