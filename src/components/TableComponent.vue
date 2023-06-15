<template>
  <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">First</th>
          <th scope="col">Last</th>
          <th scope="col">Handle</th>
        </tr>
      </thead>
      <tbody>
          <tr v-for="(item, index) in items" :key="index">
            <th scope="row">{{item.id}}</th>
            <td>{{item.fname}}</td>
            <td>{{item.lname}}</td>
            <td>
              <CommonButton :clazz="'btn-danger'" @handleSubmit="removeItem(item.id)">Delete</CommonButton>
            </td>
          </tr>
          <tr v-if="items.length==0">
            <th class="border-bottom-0"></th>
            <td colspan="3" class="border-bottom-0">
              Không có dữ liệu
            </td>
          </tr>
        </tbody>
    </table>
</template>

<script>
import CommonButton from './CommonButton.vue';
export default {
    name:'table-component',
    components:{
        CommonButton,
    },
    props:{
        items: Array
    },
    methods:{
        removeItem(val){
            this.$emit('handleSubmit', val)
        }
    }
}
</script>

<style>

</style>