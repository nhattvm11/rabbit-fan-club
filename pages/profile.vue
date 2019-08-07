<template>
    <Rabbit :username="username"/>
</template>
<script>
import Rabbit from '~/components/Rabbit.vue'

export default {
    components: {
        Rabbit,
    },
    data() {
        return {
            username: ""
        }
    },
    created() {
        this.username = this.$route.query.username
        console.log("parent")
        console.log(this.username)
    },
}
</script>
