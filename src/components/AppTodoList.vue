<template>
	<ul class="todo-list">
		<AppTodoItem
			v-for="todo in todos"
			:key="todo.id"
			:todo="todo"
			@toggle-todo="toggleTodo"
			@remove-todo="removeTodo"
		/>
	</ul>
</template>

<script lang="ts">
import { PropType, defineComponent } from "vue";
import { Todo } from "@/types/Todo";
import AppTodoItem from "@/components/AppTodoItem.vue";

export default defineComponent({
	components: {
		AppTodoItem,
	},
	props: {
		todos: {
			type: Array as PropType<Todo[]>,
		},
	},
	methods: {
		toggleTodo(id: number) {
			this.$emit("toggleTodo", id);
		},
		removeTodo(id: number) {
			this.$emit("removeTodo", id);
		},
	},
	emits: {
		toggleTodo: (id: number) => Number.isInteger(id),
		removeTodo: (id: number) => Number.isInteger(id),
	},
});
</script>

<style scoped></style>
