<template>
    <div id="show-auth"/>
</template>

<script>
    export default {
        name: "login",
        mounted() {
            this.$auth0.showLock("show-auth")
        }
    }
</script>

