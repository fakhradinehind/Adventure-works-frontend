<template lang="">
    <div class="row1">
        <navbarclient/>

    </div>
    <div class="row2">
 
        <clients/>
    </div>

</template>
<script>
    import clients from '../components/clients.vue'
    import navbarclient from '../components/Header/navbarclient.vue'
  
export default {
    components: {
        clients,
        navbarclient,
        
    }
}
</script>
<style>
    .row2{
            margin-top: 100px;
    }
</style>