<template>
  <div class="container">
    <div class="text-end">  
       <Navbar2/>
    </div>
  </div>
  <test/>
  <footer1/>
</template>
<script>
// @ is an alias to /src
import { mapActions } from 'vuex'
import test from '../components/test.vue'
import Navbar2 from '../components/Header/Navbar2.vue'
import footer1 from '../components/footer1.vue'


export default {
  components: {
    Navbar2,
    footer1,
    test
    
},
  data(){
      return{
        username:'',
        password:''
      }
  },
    name: "HomeView",
    mounted() {
        let user = localStorage.getItem("user-info");
        if (!user) {
            this.redirectTo({ val: "Signup" });
        }
        else{
          this.username=JSON.parse(user).name
          this.paasword=JSON.parse(user).password
          console.log(JSON.parse(user).name)
        }
    },
    methods: {
        ...mapActions(["redirectTo"]),
        profile(){
          this.redirectTo({ val: "Profile" });
        }
    }
}
</script>