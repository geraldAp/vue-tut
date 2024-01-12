<template>
    <a :href="page.link.url" :title="`this goes to ${page.link.text}`" aria-current="page" class="nav-link"  :class="activeClass" 
       >{{ page.link.text
        }}</a>
</template>




<script>
export default {
    props: ['page', 'isActive'],
    computed: {
        activeClass() {
            return {
                active: this.isActive,
                emphasize: this.isActive
            }
        }
    }
}

</script>

<style scoped>
.emphasize {
    text-decoration: underline !important;
}
.active{
    color: blue !important ;
}
</style>