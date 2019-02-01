<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <whale/>
    <bob/>
    <tekst tekst="Czy się uda ?"/>
  </div>
</template>

<script>
import whale from '../components/whale.vue'
export default {
    components:{
        whale
    }
}
import bob from '../components/bob.vue'
export default {
    components:{
        bob
    }
}
import tekst from '../components/tekst.vue'
export default {
    components:{
        tekst
    }
}
</script>
