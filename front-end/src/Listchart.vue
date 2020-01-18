<template>
 <h1>{{postes}}</h1>
</template>

<script>
    export default {
        props: ['postes'],
        name: 'listchart',
        data: function () {
            return {
                message: 'HELLO',
            }
        }
    }
</script>

<style>
</style>