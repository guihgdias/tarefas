<template>
  <div class="task" :class="stateClass" @click="$emit('taskStateChange', task)">
    <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
    <p>{{task.name}}</p>
  </div>
</template>

<script>
export default {
  props: {
    task: {type: Object, required: true}
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

<style scoped>
  .task {
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
    border-left: 12px solid #B73229;
    background: #F44336;
  }

  .done {
    color: #CCC;
    border-left: 12px solid #0A8F08;
    background: #4CAF50;
    text-decoration: line-through;
  }

  .pending .close {
    background: #B73229;
  }

  .done .close {
    background: #0A8F08;
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
    text-align: center;
  }

</style>