<template>
    <li class="todo-item todo-item--done" :class="{'todo-item--done': todo.completed}">
        <div class="todo-item__status">
            <i class="bi bi-check2"></i>
        </div>
        <span class="todo-item__text">{{ todo.text }}</span>
        <button class="todo-item__remove-button">
            <i class="bi bi-trash3"></i>
        </button>
    </li>
</template>

<script lang="ts">
import { Todo } from '@/models/Todo';
import { defineComponent, PropType } from 'vue';

export default defineComponent({
    props: {
        todo: {
            type: Object as PropType<Todo>,
            required: true

        }
    }
})
</script>