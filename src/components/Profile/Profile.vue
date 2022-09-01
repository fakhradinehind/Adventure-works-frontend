<template lang="">
    <div class="container">
        <Navbar />
         <form @click.prevent>
        <div class="row g-3 align-items-center">
                <h1 class="text-center">update</h1>
                <div class="col-auto d-block mx-auto">
                    <input type="text" class="form-control" placeholder="enter votre nom" v-model="name">
                    
                </div>
        </div>
        <br/>
        <div class="row g-3 align-items-center">
                 <div class="col-auto d-block mx-auto">
                    <input type="email" class="form-control" placeholder="enter votre email" v-model="email">
                   
                </div>
         </div>
    <br />
        <div class="row g-3 align-items-center">
                <div class="col-auto d-block mx-auto">
                    <input type="password" class="form-control" placeholder="enter votre mot de passe" v-model="password">
                </div>
        </div>
    <br />
        <div class="row g-3 align-items-center">
                <div class="col-auto d-block mx-auto">
                    <button type="submit" @click="update()" class="btn btn-primary">update</button>
                </div>
        </div>
    </form>
    </div>
</template>
<script>
import Navbar from '../Header/Navbar.vue'
export default {
    components:{
        Navbar
    },
    methods:{
        update() {

            
        },
    },
    data(){
        return{
            name:'',
            email:'',
            password:''
        }
    },
    mounted(){
        let user=localStorage.getItem("user-info")
        if(user){
            this.name=JSON.parse(user).name
            this.email=JSON.parse(user).email
            this.password=JSON.parse(user).password
        }
        else{
            console.log("hello")
        }
    }
}
</script>
<style lang="">
    
</style>