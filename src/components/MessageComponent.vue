<template>
  <div :class="clazz">{{ message }}</div>
</template>

<script>
export default {
    name: 'message-component',
    props:{
        message:{
            type:String,
            default:""
        },
        clazz: String
    }
}
</script>

<style>

</style>