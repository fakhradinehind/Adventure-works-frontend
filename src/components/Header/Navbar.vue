<template lang="">
    <div class="float-right ">
        <ul id="nav">
                <router-link tag="li" :to="{name :'home',params :{pagetitle :'home'}}" exact>
                    <a>Home</a>
                </router-link>
                <a href="#" @click="logout()">Logout</a>
        </ul>
    </div>
</template>
<script>
export default {
    name:"Navbar",
    methods:{
        logout(){
            localStorage.clear();
            this.$router.push({name :'Login'})
        }
    }
    
}
</script>
<style lang="scss" scoped>
$fontColor:darkcyan;
$navColor:#525a5a;

ul{
    display: flex;
    justify-content:center;
    list-style: none;
    margin-bottom: 50px;
    a{
        text-decoration:none;
        font-weight:bold;
        color:$fontColor;
        padding:10px;
    }
}
a.router-link-exact-active a,ul a a:hover{
    color:$navColor;
    box-shadow: 2px 2px 4px 0px $navColor;
}
    
</style>