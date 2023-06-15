<template>
  <div id="app">
    <h2>Form:</h2>
    <InputField
      @onChange="changeFirstName"
      :placeholderText="'FirstName'"
      :valueInput="firstname"
      :isSubmit="isSubmit"
      @changeSubmitState="changeSubmitState"
    />
    <InputField
      @onChange="changeLastName"
      :placeholderText="'LastName'"
      :valueInput="lastname"
      :isSubmit="isSubmit"
    />
    <MessageComponent :class="clazz" v-if="isError" :message="message" />
    <MessageComponent :class="clazz" v-if="isSubmit" :message="message" />
    <br />

    <CommonButton @handleSubmit="addItem" :clazz="'btn-success'"/>

    <br />
    <br />
    <TableComponent :items="items" @handleSubmit="removeItem" />
  </div>
</template>

<script>
import InputField from "./components/InputField.vue";
import CommonButton from "./components/CommonButton.vue";
import TableComponent from "./components/TableComponent.vue";
import MessageComponent from "./components/MessageComponent.vue";
// import { timeStamp } from "console";

export default {
  name: "App",
  components: {
    InputField,
    CommonButton,
    TableComponent,
    MessageComponent,
  },
  data() {
    return {
      firstname: "",
      lastname: "",
      isError: false,
      message: "",
      isSubmit: null,
      clazz: "",
      items: [
        {
          id: 1,
          fname: "Mark",
          lname: "Otto",
        },
        {
          id: 2,
          fname: "Jacob",
          lname: "Thornton",
        },
        {
          id: 3,
          fname: "Lazy",
          lname: "Bird",
        },
      ],
    };
  },
  watch: {},
  methods: {
    changeFirstName(data) {
      this.firstname = data;
      this.isError = false;
    },
    changeLastName(data) {
      this.lastname = data;
      this.isError = false;
    },
    addItem() {
      if (this.firstname === "" || this.lastname == "") {
        this.isError = true;
        this.message = "Không được để trống!";
        this.clazz = "messageError";
        this.isSubmit = false;
      } else {
        this.isSubmit = true;
        this.isError = false;
        this.clazz = "messageSuccess";
        this.message = "Bạn đã thêm thành công";
        const data = {
          id: this.items.length + 1,
          fname: this.firstname,
          lname: this.lastname,
        };
        this.items.push(data);
      }
    },
    removeItem(val) {
      this.items = this.items.filter((item) => item.id != val);
    },
    changeSubmitState(val) {
      this.isSubmit = val;
    },
  },
};
</script>

<style>
.messageError {
  color: red;
}
.messageSuccess {
  color: green;
}
</style>
