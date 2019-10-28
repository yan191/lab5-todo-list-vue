<template>
    <div class="index">
        <TopBannerInput :tasks.sync="tasks" ></TopBannerInput>
        <TaskList :tasks.sync="tasks"></TaskList>
    </div>
</template>

<script>
import TopBannerInput from '@/components/TopBannerInput.vue'
import TaskList from '@/components/TaskList.vue'

export default {
    name: 'index',
    components: {
        TopBannerInput,
        TaskList
    },
    data () {
        return {
            tasks: []
        }
    }
}
</script>