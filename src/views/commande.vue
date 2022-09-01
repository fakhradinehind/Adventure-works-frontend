<template lang="">
    <div class="row1">
        <navbarcommande/>
    </div>
    <div class="row2">
        <commande/>
    </div>
</template>
<script>
    import navbarcommande from '../components/Header/navbarcommande.vue'
    import commande from '../components/commande.vue'
export default {
    components: {
        commande,
        navbarcommande

    }
}
</script>
<style>
      .row2{
            margin-top: 100px;
    }
</style>