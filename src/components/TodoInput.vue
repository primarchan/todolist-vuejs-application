<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: ''
    }
  },
  methods: {
    addTodo() {
      // input box의 값이이 있을 때만 저장
      if(this.newTodoItem !== "") {
        // input box에 입력된 텍스트의 앞뒤 공백 문자열 제거
        var value = this.newTodoItem && this.newTodoItem.trim();
        // localStorage.setItem(value, value);
        this.$emit('addTodo', value);
        // input box의 입력 값을 초기화
        this.clearInput();
        }
      },
      clearInput() {
        this.newTodoItem = '';
      }
  }

}
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: inline-block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>