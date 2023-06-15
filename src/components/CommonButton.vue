<template>
  <div ml-2>
    <button 
      type="button" 
      class="btn"
      :class="clazz"
      @click="handleSubmit"
    >{{ clazz=='btn-danger'?'Delete':"Add" }}</button>
  </div>
</template>

<script>
export default {
  props:{
    clazz: String
  },
  methods:{
    handleSubmit(val){
      this.$emit('handleSubmit', val)
    }
  }
};
</script>

<style></style>
