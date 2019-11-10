<template>
    <div id="gpa">
        <strong>{{ user.gpa }}</strong>
    </div>
</template>

<script>
    export default {
        name: "GPA",
        props: {
            user: Array,
        }
    }
</script>

<style scoped>

</style>