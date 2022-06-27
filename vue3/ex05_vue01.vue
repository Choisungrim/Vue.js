<template>
    <div>
        My Header message => <span>{{message}}</span>
    </div>
</template>

<script>
export default {
    data(){return {message : 'test 중 입니다 ...'}}
}
</script>

<style scoped>
    span{
        font-size: 1.2em;
    }
</style>