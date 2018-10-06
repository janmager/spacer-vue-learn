<template>
    <div class="claimWrapper">
        <h1 class="claim">SPACER</h1>
        <p class="subclaim">
            Begin your journey throught our amazing galaxy,
            nad discover places you never even heard of.
        </p>
        <p class="subclaim">
            Type anything space-related to start.
        </p>
    </div>
</template>

<script>
    export default {
        name: 'Claim',
    }
</script>

<style land="scss" scoped>
    .claimWrapper{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
    .claim{
        font-size: 50px;
        margin: 0;
        font-weight: 800;
    }
    .subclaim{
        margin: 15px 0 0 0;
        font-size: 13px;
    }
</style>
