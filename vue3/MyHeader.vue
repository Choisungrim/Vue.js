<template>
    <div>My Header message => {{ mesage }}</div>
<template>   
<!-- 
** template 
=> 화면에 표시할 요소들을 정의하는 영역
=> Html + Vue 데이터 바인딩
 -->

<script>
export default {
    data: {
        message: 'test 중 입니다 ...'
    }
}
</script> 
<!--
** script 
=> Vue 컴포넌트의 내용을 정의하는 영역
=> data, method 등 

** style
=> template 에 추가한 Html Tag 의 CSS 스타일을 정의 
=> vue 의 스타일로 아래의 특성이 있음
    
1) Scoped CSS
=> scoped 를 설정할 경우 해당 vue 안에서만 적용됨
=> Vue.js의 내장 기능이 아니라 vue-loader 에서 제공하는 기능이며,
    vue-loader 는 Single-File Components (SFCs) 포맷으로 코드를 작성할 수 있도록 도와주는 도구이다.
    즉 Scoped CSS는 SFC 로 작성할 경우 해당됨. 
    
2) language 설정 
=> lang='scss'  
=> 설정에 따라 style 컴파일 방법이 달라짐 
-->

<style scoped>
    span {
        font-size:1.2em;
    }

</style>  