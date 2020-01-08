<template>
  <div class="test">
    <Toolbar msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Toolbar from '@/components/Toolbar.vue'
//import Navbar from '@/components/Navbar.vue'

export default {
  name: 'test',
  components: {
    Toolbar,//Navbar,
  }
}
</script>
