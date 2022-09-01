<template lang="">
     <div class="row1">
        <navbartemps/>
    </div>
    <div class="row2">
        <temps/>
    </div>
</template>
<script>
    import temps from '../components/temps.vue'
    import navbartemps from '../components/Header/navbartemps.vue'
export default {
    components: {
        temps,
        navbartemps
        }
}
</script>
<style>
     .row2{
            margin-top: 100px;
    }
</style>