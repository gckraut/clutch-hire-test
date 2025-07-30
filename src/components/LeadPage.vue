<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{ msg2 }}</h2>
    <form v-on:submit.prevent="submitForm" method="post" id="myForm">
      <div>
        <h3>First Name</h3>
        <input
          type="text"
          v-model="formData.first"
          name="first"
          id="first"
        />
      </div>
      <div>
        <h3>Last Name</h3>
        <input
          type="text"
          v-model="formData.last"
          name="last"
          id="last"
        />
      </div>
      <div>
        <h3>Email</h3>
        <input
         type="text"
         v-model="formData.email"
         name="email"
         id="email"
        />
      </div>
      <div>
        <h3>Phone Number</h3>
        <input type="text" v-model="formData.phone" name="phone" id="phone" />
      </div>
      <div>
        <h3>Company</h3>
        <input type="text" v-model="formData.company" name="company" id="company" />
      </div>
      <div class="button">
      <button type="submit">Continue</button>
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import axios from 'axios';

export default defineComponent({
  name: "LeadPage",

  data() {
   return {
    formData:{
     first:null,
     last:null,
     email:null,
     phone:null,
     company:null
    },
    msg: 'Have us reach out',
    msg2: ''
   }
  },
  methods: {
    async submitForm() {
      try {
        const response = await axios.post("https://dev-api-api.hiring-test.experientialpreview.com/api/lead/9c17635d-be35-4ffc-9265-cbdd9044e64d", this.formData);
        console.log('Form submitted successfully:', response.data);
        this.msg = 'Thank you'; // This will automatically update the displayed text
        this.msg2 = 'We will contact you shortly';
        // Handle success, e.g., show a success message
        setTimeout(() => {this.msg = ""; this.msg2 = ""; this.formData.first = null; this.formData.last = null; this.formData.email = null;
         this.formData.phone = null;  this.formData.company = null; }, 5000);
      } catch (error) {
        console.error('Error submitting form:', error);
          this.msg = 'Error submitting form';
          setTimeout(() => {this.msg = "";}, 5000);
        // Handle error, e.g., show an error message
      }
    }
  }
});
 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h1 {
  font-family: 'Roboto', sans-serif;
  font-weight: 400;
  color: #555552;
  margin-top: 138px;
}
h2 {
  font-family: 'Roboto', sans-serif;
  font-weight: 400;
  color: #555552;
}
input {
    width: 310px;
    height: 40.32px;
    border: 0.72px solid #555552;
    font-family: 'ABeeZee', sans-serif;
    border-radius: 3.6px;
}
h3 {
  margin: 10px 0 0;
  font-family: 'ABeeZee', sans-serif;
  font-size: 12px;
  color: #006315;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
button {
    background-color: #0B476C;
    color: #FFFFFF;
    line-height: 16px;
    font-size: 13.45px;
    font-family: 'ABeeZee', sans-serif;
    border-radius: 4px;
    padding: 10.22px 37.5px 8.61px 37.5px;
}
div.button {
    margin-top: 10px;
    align: right;
}
</style>
