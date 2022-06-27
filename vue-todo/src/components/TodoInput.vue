<template>
  <div class="inputBox shadow">
    <input
      type="text"
      placeholder="일정을 입력 하세요 ~~"
      v-model="newTodoItem"
      v-on:keypress.enter="addTodo"
    />
    <!-- 
		 <button v-on:click="addTodo">추가</button> 
	 ** button 대신 + 사용으로 변경 -->
    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>

    <!-- Modal 컴포넌트 등록 -->
    <modal v-if="showModal" @close="showModal = false">
      <h3 slot="header">경고</h3>
      <span slot="footer" @click="showModal = false"
        >일정을 입력하세요.
        <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
      </span>
    </modal>
  </div>
</template>

<script>
// ** Modal 띄우기
// => Modal 컴포넌트 등록 ( components: ~~~ , import Modal from ~~~~ )
// => template 에 Modal 컴포넌트 추가
// => addTodo() 에 코드, data 에  showModal 속성 추가

import Modal from "./common/Modal.vue";

export default {
  data() {
    return {
      newTodoItem: "",
      showModal: false, //모달동작을 위한 flag 값
    };
  },
  methods: {
    addTodo() {
      console.log("** newTodoItem => " + this.newTodoItem);
      // ** ver01 : (입력값 확인없이) 로컬 스토리지에 저장
      //localStorage.setItem(this.newTodoItem,this.newTodoItem);

      /* ** ver02 : 예외코드 추가
			// => input 에 입력값이 있는 경우에만 저장
			// => input 의 입력값의 앞 뒤 공백 제거
			// => input 의 입력값 초기화	
			if (this.newTodoItem !=="") {
				//var value = this.newTodoItem && this.newTodoItem.trim();
				var value = this.newTodoItem.trim();
				localStorage.setItem(value, value);
				this.clearInput();
			}; //if
			*/
      // ** ver03 : Modal 추가
      if (this.newTodoItem !== "") {
        var value = this.newTodoItem.trim();
        localStorage.setItem(value, value);
        //this.$emit('addTodo', value);
        this.clearInput();
      } else {
        //=> 일정 텍스트 미입력 시 모달 동작 : this.showModal 를 true 가 되도록
        this.showModal = !this.showModal;
      }
    }, //addTodo
    clearInput() {
      this.newTodoItem = "";
    }, //clearInput
  }, //methods
  components: {
    Modal: Modal, // 모달 컴포넌트 등록
  }, //components
};
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
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>
