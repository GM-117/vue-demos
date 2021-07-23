<template>
  <div :class="['item', todo.completed? 'completed': '']">
    <input type="checkbox" class="toggle" v-model="todo.completed" />
    <label for="">{{ todo.content }}</label>
    <button class="destroy" @click="deleteTodo"></button>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  methods: {
    deleteTodo() {
      this.$emit("del", this.todo.id);
    },
  },
};
</script>

<style scoped>
.item {
  position: relative;
  background-color: #fff;
	font-size: 24px;
	/* height: 48px; */
	border-bottom: 1px solid rgba(0, 0, 0, 0.06);
}
.completed > label{
	color: #d9d9d9;
	text-decoration:line-through
}
.toggle{
	text-align: center;
	width: 50px;
	height: 20px;
	position: absolute;
	top: 0;
	left: 0;
	/* margin: auto 0; */
	margin-top: 15px;
}
label{
	height: 24px;
	/* margin: auto 0; */
	padding: 15px 60px 15px 15px;
	display: block;
	line-height: 24px;
}
.destroy{
	position: absolute;
	top: 0;
	right: 10px;
	border: none;
	background: none;
	font-size: 30px;
	color: rgba(175,47,47,0.4);
	margin-top: 10px;
}
.destroy:hover{
	cursor: pointer;
	color: rgba(175,47,47,0.6);
}
.destroy::after{
	content:'×'
}
</style>