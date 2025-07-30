<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/greentech.png" />
    <LeadPage msg="Have us reach out" msg2=""  />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

import LeadPage from "@/components/LeadPage.vue"; // @ is an alias to /src

export default defineComponent({
  name: "HomeView",
  components: {
    LeadPage,
  },
});
</script>
<style scoped lang="scss">

h3 {
  margin: 40px 0 0;
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
img {
  max-height: 40px; 
  margin-top: 30px;
}
</style>
