<template>
  <v-alert>
      <h1>
       <div> <img alt="Vue logo" src="http://www.vstecs.co.th/en/images/vstecs-logo-02.png"></div>
        <span class="text-navy"> Enterprise system </span>
          <small> This is presales performance report system </small>
          </h1>
          <p>If see someting worng please contact wanchai@vstecs.co.th to fix it</p>
          <h2>รบกวนตรวจสอบความถูกต้องของรายงานด้วย</h2>
          <div class="text-center">
          <v-btn a href="/about" rounded color="primary" dark>click here to login</v-btn>
          </div>
    </v-alert>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: () => ({
    
  }),
};
</script>

