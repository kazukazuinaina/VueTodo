<template>
<div>
    <ul>
    <input class=counter v-model="task" placeholder="追加するタスクを入力">
    <p>Add task: {{ task }}</p>
    <button  v-on:click="addNewTodo">タスクを追加</button>
        <li v-for="task in list" v-bind:key="task.id">
            <br>
            {{ task.id }} {{ task.name }}
            <select v-model="task.id">
                <option v-for="option in options" v-bind:value="task.id">
                    {{ option.text }}
                </option>
            </select>
            <button  v-on:click="deleteTodo(task)">タスクを削除</button>

        </li>
    </ul>
</div>
</template>

<script>
export default {
  data () {
      return {
          //初期化
          task: '',
          list: [
            ],
          selected: '',
          options: [
              { text: '優先度を入力', value: 'A' },
              { text: '優先度: 低い', value: 'B' },
              { text: '優先度: 中程度', value: 'C' },
              { text: '優先度: 高い', value: 'D' }
            ],
        };
    },
methods: {
    addNewTodo () {
      this.list.push({
        id: this.list.length + 1,
        name: this.task,
        //priorityは優先度
        priority: this.task
      });
      this.task = '';
    },
    deleteTodo (task) {
        var index = this.list.indexOf(task)
        this.list.splice(index, 1) 
    }
  },
}
</script>

<style scoped>
.counter {
    font-size: 26px;
    background-color: #dfd;

}
</style>