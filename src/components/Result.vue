<template>
    <p>Your result is {{ score }} ms</p>
    <div v-if="score<250">
        <p>OMG You are awesome.</p>
    </div>
    <div v-else-if="score>250 && score<1000">
        <p>Not bad guy . Keep going.</p>
    </div>
    <div v-else="score>1000">
        <p>Slow clicking . Keep trying more.</p>
    </div>
</template>

<script>
    export default{
        props : ['score']
    }
</script>

<style></style>