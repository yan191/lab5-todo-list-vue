<template>
    <div class="top-banner-input">
        <h1>Lab5 - vue.js</h1>

        <div class="add-task">
            <div class="input">
                <input type="text" placeholder="type a task to add..." v-model="task">
            </div>

            <div class="btn-add" @click="addTask">add</div>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue, Prop, Emit } from 'vue-property-decorator'


@Component
export default class TopBannerInput extends Vue {

    @Prop() tasks: string[] = [];
    task: string = '';

    addTask(): void {
        if (this.task.length === 0) {
            alert('Task vazia');
            return;
        }

        this.updateTasks();
    }

    @Emit('update:tasks') updateTasks() {
        this.tasks.push(this.task);
        this.task = '';
        return this.tasks;
    }
}
</script>

<style scoped>
    .top-banner-input {
        width: 100vw;
        min-height: 45vh;
        background-image: url('../assets/banner.jpg');
        background-size: cover;
        background-position: center center;
        background-repeat: no-repeat;
        position: relative;
        margin-top: 0;
    }
    .top-banner-input:after {
        content: ' ';
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background-color: rgba(153, 46, 36, .5);
        position: absolute;
    }

    .top-banner-input h1 {
        position: relative;
        font-size: 50px;
        text-transform: uppercase;
        color: #fff;
        margin: 0;
        padding:50px 0;
        z-index: 2;
        text-align: center;
    }

    .top-banner-input .add-task {
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        z-index: 2;
    }

    .top-banner-input .input {
        display: flex;
        justify-content: flex-end;
        align-items: center;
        width: 400px;
        height: 50px;
        border-top-left-radius: 10px;
        border-bottom-left-radius: 10px;
        background-color: #fff;
        overflow: hidden;
    }

    .top-banner-input .input:hover {
        cursor: pointer;
    }

    .top-banner-input .input input{
        width: 95%;
        height: 100%;
        margin: 0;
        border: none;
        box-shadow: none;
        outline: 0;
        font-size: 18px;
    }

    .btn-add {
        width: 90px;
        height: 50px;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #D03D16;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        font-size: 18px;
        text-transform: uppercase;
        color: #fff;
        overflow: hidden;
    }

    .btn-add:hover {
        cursor: pointer;
        background-color: rgb(177, 55, 22);
    }
</style>