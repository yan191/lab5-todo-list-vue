<template>
    <div class="task-list">
        <div class="title">Your to do list</div>

        <ol class="list">
            <li class="task" v-for="(task,index) in tasks" :key="index" @click="removeTask(index)">{{ task }}</li>
        </ol>
    </div>
</template>

<script lang="ts">
import { Component, Vue, Prop, Emit } from 'vue-property-decorator'

@Component
export default class TaskList extends Vue {

    @Prop() tasks: string[] = [];

    @Emit('update:tasks') removeTask(index: number) {
        const newTasks: string[] = [];
        for (let i = 0; i < this.tasks.length; i++) {
            if (index != i) {
                newTasks.push(this.tasks[i]);
            }
        }
        return newTasks;
    }
}
</script>

<style scoped>
    .title {
        width: calc(95% - 20px);
        margin: auto;
        border-bottom: 1px solid #D03D16;
        text-align: left;
        color: #D03D16;
        font-size: 18px;
        padding: 15px 10px 5px;
    }

    .task-list {
        width: 600px;
        min-height: 40vh;
        margin: -5vh auto 50px;
        background-color: #fff;
        border-radius: 10px;
        position: relative;
        z-index: 999;
    }

    .task-list .list .task {
        text-align: left;
        font-size: 16px;
    }

    .task-list .list .task:hover {
        cursor: pointer;
        color: #D03D16;
        text-decoration: line-through;
    }
</style>