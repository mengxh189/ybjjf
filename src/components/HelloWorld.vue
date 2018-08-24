<template>
  <div class="hello">
  <div>
    <input type="text" v-model="inputValue" @keyup.enter="handerBtnClick"/>
    <button @click="handerBtnClick">提交</button>
  </div>
    <ul>
      <todo-item v-bind:key="item"
                 :content="item"
                 :index="index"
                 v-for="(item, index) in list"
      @delete="handerItemDelete"></todo-item>
    </ul>
  </div>
</template>

<script>

var TodoItem = {
  props: ['content', 'index'],
  template: '<li @click="handerItemClick">{{content}}</li>',
  methods: {
    handerItemClick () {
      this.$emit('delete', this.index)
    }
  }
}
export default {
  name: 'HelloWorld',
  components: {
    TodoItem: TodoItem
  },
  data () {
    return {
      inputValue: '',
      list: []
    }
  },
  methods: {
    handerBtnClick: function () {
      this.list.push(this.inputValue)
      this.inputValue = ''
    },
    handerItemDelete: function (index) {
      this.list.splice(index, 1)
    }
  }
}
</script>

<style scoped>

</style>
