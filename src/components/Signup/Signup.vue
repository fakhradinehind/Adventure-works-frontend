<template lang="">
    <form @click.prevent>
        <div class="row g-3 align-items-center">
                <h1>Sign Up</h1>
                <div class="col-auto d-block mx-auto">
                    <input type="text" class="form-control" placeholder="enter votre nom" v-model="name">
                    <span class="error-feedback" v-if="v$.name.$error">
                        {{v$.name.$errors[0].$message}}
                    </span>
                </div>
        </div>
        <br/>
        <div class="row g-3 align-items-center">
                 <div class="col-auto d-block mx-auto">
                    <input type="email" class="form-control" placeholder="enter votre email" v-model="email">
                    <span class="error-feedback" v-if="v$.email.$error">
                        {{v$.email.$errors[0].$message}}
                    </span>
                </div>
         </div>
    <br />
        <div class="row g-3 align-items-center">
                <div class="col-auto d-block mx-auto">
                    <input type="password" class="form-control" placeholder="enter votre mot de passe" v-model="password">
                    <span class="error-feedback" v-if="v$.password.$error">
                        {{v$.password.$errors[0].$message}}
                    </span>
                </div>
        </div>
    <br />
        <div class="row g-3 align-items-center">
                <div class="col-auto d-block mx-auto">
                    <button type="submit" @click="signup()" class="btn btn-primary">Sign Up Now</button>
                    &nbsp;&nbsp;&nbsp;
                    <button type="submit" class="btn btn-link" @click="redirectTo({val :'Login'})">Login</button>
                </div>
        </div>
    </form>

</template>
<script>
import { mapActions } from 'vuex'
import axios from 'axios'
import useValidate from '@vuelidate/core'
import {required,email,minLength} from '@vuelidate/validators'
import { assertExpressionStatement } from '@babel/types'
export default {
    name:"Signup",
    data(){
        return{
            v$: useValidate(),
            name:'',
            email:'',
            password:''

        }
    },
    validations(){
        return{
            name:{required,minLength:minLength(10)},
            email:{required,email},
            password:{required,minLength:minLength(10)}
        }
    },
  
    methods:{
        ...mapActions(['redirectTo']),
        async signup (){
            this.v$.$validate()
            if(!this.v$.$error){
                console.log('validate successfully')
                let result =await axios.post('http://localhost:3000/users',{
                    name:this.name,
                    email:this.email,
                    password:this.password
                })
                if(result.status==201){
                    console.log('added new user succeess')
                    localStorage.setItem("user-info",JSON.stringify(result.data))
                    console.log(result.data)
                    this.redirectTo({val :"home"})
               }
                else{
                    console.log("error in added user")
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
   height:420px;
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
    font-weight: bold;
    }
</style>