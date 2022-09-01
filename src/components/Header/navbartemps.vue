<template lang="">
    <div>
        <nav  class="navbar navbar-expand-lg navbar-light bg-white py-3 shadow-sm fixed-top">
        <div class="navlogo">
            <img id="logo" src="../../assets/logo2.png">
            <h2 id="h2logo">NexaStack</h2>
        </div>
        <button type="button" data-toggle="collapse" data-target="#navbarContent" aria-controls="navbars" aria-expanded="false" aria-label="Toggle navigation" class="navbar-toggler">
                <span class="navbar-toggler-icon"></span>
            </button>
        <div id="navbarContent" class="collapse navbar-collapse">
          <ul class="navbar-nav mx-auto">
            <!-- Megamenu-->
          

            <li class="nav-item"><router-link to="/" class="nav-link font-weight-bold" style="font-family: 'Montserrat', sans-serif; color: black; margin-left: 7px; margin-right: 7px;">Home</router-link></li>
            <li class="nav-item"><router-link to="/clients" class="nav-link font-weight-bold" style="font-family: 'Montserrat', sans-serif; color: black; margin-left: 7px; margin-right: 7px;"  @click="Clients()">Clients</router-link></li>
            <li class="nav-item"><router-link to="/produits" class="nav-link font-weight-bold" style="font-family: 'Montserrat', sans-serif; color: black; margin-left: 7px; margin-right: 7px;"  @click="Produits()">Produits</router-link></li>
            <li class="nav-item"><router-link to="/employes" class="nav-link font-weight-bold" style="font-family: 'Montserrat', sans-serif; color: black; margin-left: 7px; margin-right: 7px;"  @click="Employes()">Employes</router-link></li>
            <li class="nav-item"><router-link to="" class="nav-link font-weight-bold" style="font-family: 'Montserrat', sans-serif; color: black; margin-left: 7px; margin-right: 7px;"  @click="Regions()">Regions</router-link></li>
            <li class="nav-item"><router-link to="" class="nav-link font-weight-bold" style="font-family: 'Montserrat', sans-serif; color: #007bff; margin-left: 7px; margin-right: 7px;" @click="logout()">Logout</router-link></li>
            
          </ul>
        </div>
      </nav>
    </div>
</template>
<script>
export default {
    
}
</script>
<style lang="">
    
</style>