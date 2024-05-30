<script>
export default{
    name:"NavBarButton",
    props: ['text'],
}
</script>

<template>
<div>
    {{ text }}
</div>
</template>

<style lang="scss" scoped>
div{
    color: white;
}
</style>