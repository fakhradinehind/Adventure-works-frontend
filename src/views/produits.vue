<template lang="">
    <div class="row1">
        <navbarproduit/>
    </div>
    <div class="row2">
        <produits/>
    </div>
    <div>
        <footer1/>
    </div>
</template>
<script>
    import produits from '../components/produits.vue'
    import navbarproduit from '../components/Header/navbarproduit.vue'
    import footer1 from '../components/footer1.vue'
export default {
    components: {
        produits,    
        navbarproduit,
        footer1
    }
}
</script>
<style>
     .row2{
            margin-top: 100px;
    }
</style>