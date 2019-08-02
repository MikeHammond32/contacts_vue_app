<template>
  <div class="home">
    <h1>{{ message }}</h1>
      <p>FirstName: <input type="text" v-model="newContactFirstName"></p>
   <p>last_name: <input type="text" v-model="newContactLastName"></p>
   <p>PhoneNumber: <input type="text" v-model="newContactPhoneNumber"></p>
   <p>Email: <input type="text" v-model="newContactemail"></p>
   <button v-on:click="makeContact()">Make a new contact</button>

  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "change.js",
      contacts: [],
      newContactFirstName: "",
      newContactLastName: "",
      newContactPhoneNumber: "",
      newContactEmail: "",
      currentContact: {}

    };
  },
  created: function() {
    console.log('in created');
    axios.get("/api/products").then(response => {
      console.log(response.data);
      this.contacts = response.data;
    })
    
  },
  methods: {
    makeContact: function() {
      console.log('in make Contact');
      var newContact = {
        First_name: this.newContactFirstName,
        Last_name: this.newContactLastName,
        Email: this.newContactEmail,
        Phone_Number: this.newContactPhoneNumber
      }
    }
  }
};
</script>
