<template>
  <div>
    <ul>
      <li v-for="(item, index) in propsdata" :key="item.item" class="shadow">
        <i
          class="far fa-check-square checkBtn"
          v-bind:class="{ checkBtnCompleted: item.completed, testClass }"
          v-on:click="toggleComplete(item, index)"
        ></i>
        <span v-bind:class="{ textCompleted: item.completed }">
          {{ item.item }}
        </span>
        <span class="removeBtn" v-on:click="removeTodo(item, index)">
          <i class="fas fa-trash"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["propsdata"],
  data: function() {
    return {
      todoItems: [],
      testClass: true,
    };
  },
  methods: {
    removeTodo: function(todoItem, index) {
      this.$emit("removeItem", todoItem, index);
    },
    toggleComplete: function(item, index) {
      this.$emit("completeItem", item, index);
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
</style>
