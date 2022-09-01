<template lang="">
    <form @click.prevent>
        <div class="row g-3 align-items-center">
                <h1>login</h1>
                <div class="col-auto d-block mx-auto">
                    <input type="email" class="form-control" placeholder="enter votre email" v-model="email">
                    <span class="error-feedback" v-if="v$.email.$error">{{v$.email.$errors[0].$message}}</span>
                </div>
         </div>
    <br />
        <div class="row g-3 align-items-center">
                <div class="col-auto d-block mx-auto">
                    <input type="password" class="form-control" placeholder="enter votre mot de passe" v-model="password">
                    <span class="error-feedback" v-if="v$.password.$error">{{v$.password.$errors[0].$message}}</span>
                </div>
        </div>
    <br />
        <div class="row g-3 align-items-center">
                <div class="col-auto d-block mx-auto">
                    <button type="submit" class="btn btn-primary" @click="login()">Login</button> 
                     &nbsp;&nbsp;&nbsp;
                    <button type="submit" class="btn btn-link" @click="redirectTo({val :'Signup'})">Sign Up</button>
                </div>
        </div>
        <span v-if="response" class="error-feedback">{{userNotFound}}</span>
    </form>
</template>
<script>
import { mapActions } from 'vuex'
import axios from 'axios'
import useVuelidate from '@vuelidate/core'
import {required,email,minLength} from '@vuelidate/validators'
export default {
    name:"Signup",
    data(){
        return{
            v$:useVuelidate(),
            password:'',
            email:'',
            response:false,
            userNotFound:'user not found'
        }
    },
    
    validations(){
        return{
            password:{required,minLength:minLength(10)},
            email:{required,email}
        }
    },
     mounted() {
        let user=localStorage.getItem("user-info")
        if(user){
             this.redirectTo({val :"home"})
        }
    },
    methods:{
        ...mapActions(['redirectTo']),
       async login (){
            this.v$.$validate()
            if(!this.v$.$error){
                console.log('validate successfully')
                let result=await axios.get(`http://localhost:3000/users?email=${this.email}&password=${this.password}`)
                
            if(result.status==200 && result.data.length>0){
                localStorage.setItem("user-info",JSON.stringify(result.data))
                console.log('loged in')
                this.redirectTo({val:'home'})
            
            }
            else{
                console.log('no user found')
                this.response=true
            }
            }
            else{
                console.log("form validator failed")
            }
        }

    }
}
</script>
<style scoped>
form{
    background-color: #EDF1FD;
    width:40%;
   height:350px;
    margin-left: auto;
    margin-right: auto;
    margin-top:150px;
    
}
.error-feedback{
    color:red;
    font-size:11px;
}
h1{
    text-align:center;
    font-weight:bold;
}
</style>