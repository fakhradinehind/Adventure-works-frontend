<template lang="">
    <div class="row1">
        <navbaremployes/>
    </div>
    <div class="row2">
        <employes/>
    </div>
    <div>
        <footer1/>
    </div>
</template>
<script>
    import employes from '../components/employes.vue'
    import navbaremployes from '../components/Header/navbaremployes.vue'
    import footer1 from '../components/footer1.vue'
export default {
    components: {
        employes,
        navbaremployes,
        footer1
    }
}
</script>
<style>
    .row2{
        margin-top: 100px;
    }
</style>