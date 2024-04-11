<template>
  <div 
    @click="$emit('taskStateChanged', task)"
    class="task-component"
    :class="stateClass">
    <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
    <p>{{ task.name }}</p>
  </div>
</template>

<script>
export default {
    props: {
        task: {
            type: Object,
            required: true
        }
    },
    computed: {
        stateClass() {
            return {
                pending: this.task.pending,
                done: !this.task.pending
            } 
        }
    }
}
</script>

<style>
    .task-component {
        position: relative;
        box-sizing: border-box;
        width: 350px;
        height: 150px;
        padding: 10px;
        border-radius: 8px;
        font-size: 2rem;
        font-weight: 300;
        cursor: pointer;
        user-select: none;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .pending {
        border-left: 12px solid #b73229;
        background-color: #D2B48C;
        
    }

    .done {
        color: #ddd;
        border-left: 12px solid #0a8f08;
        background-color: #D2B48C;
        text-decoration: line-through;
    }

    .pending .close {
        background-color: #b73229;
    }

    .done .close {
        background-color: #0a8f08;
    }

    .close {
        position: absolute;
        right: 10px;
        top: 10px;
        font-size: 0.9rem;
        font-weight: 600;
        height: 20px;
        width: 20px;
        border-radius: 50%;
        display: flex;
        justify-content: center;
    }

    .pending .close:active {
        background-color: #D2B48C;
        
    }

    .done .close:active {
        background-color: #D2B48C;
    }
</style>