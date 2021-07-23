<template>
  <div class="footer">
    <span class="left">{{ this.unfinishedTodo.length }} items left</span>
    <span class="foot-tabs">
      <span
        v-for="state in states"
        :key="state"
        :class="[state, filter == state ? 'actived' : '']"
        @click="toggleFilter(state)"
      >
        {{ state }}
      </span>
    </span>
    <span class="clear" @click="clearAllCompleted">Clear Completed</span>
  </div>
</template>

<script>
export default {
  props: {
    filter: {
      type: String,
      required: true,
    },
    todos: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      states: ["all", "active", "completed"],
    };
  },
  computed: {
    unfinishedTodo() {
      let nums = this.todos.filter((todo) => todo.completed == false);
      console.log(nums);
      return nums;
    },
  },
  methods: {
    clearAllCompleted() {
      this.$emit("clearAll");
    },
    toggleFilter(state) {
      this.$emit("toggle", state);
    },
  },
};
</script>

<style scoped>
.footer {
  height: 30px;
  display: flex;
  font-weight: 100;
  justify-content: space-between;
  padding: 5px 0;
  line-height: 30px;
  font-size: 15px;
  box-shadow: 0 1px 1px rgb(0 0 0 / 20%), 0 8px 0 -3px #f6f6f6,
    0 9px 1px -3px rgb(0 0 0 / 20%), 0 16px 0 -6px #f6f6f6,
    0 17px 2px -6px rgb(0 0 0 / 20%);
}
.left,
.foot-tabs,
.clear {
  padding: 0 10px;
}
.foot-tabs {
  width: 200px;
  display: flex;
  justify-content: space-between;
}
.foot-tabs > span{
	/* display: inline-block; */
	padding: 0 5px;
	/* border: 1px solid rgba(175, 47, 47, 1); */
}
.foot-tabs,
.clear {
  cursor: pointer;
}
.foot-tabs > span.actived {
	border: 1px solid rgba(175, 47, 47, 0.8);
  border-radius: 5px;
}
</style>