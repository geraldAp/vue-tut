<template>
    <Navbar :pages="pages" :active-page="activePage" :nav-link-click="(index) => activePage = index" />

    <page-viewer
    v-if="pages.length > 0"
    :page="pages[activePage]">
    </page-viewer>
</template>



<script>
import PageViewer from './components/PageViewer.vue';
import Navbar from './components/Navbar.vue';

export default {
    // object containing the components we use inside vue 
    components: {
        Navbar,
        PageViewer
    },

    data() {
        return {
            activePage: 0,
            pages: [],
        };
    },
    created() {
        this.getPage()
    },
    methods: {
        async getPage() {
            let res = await fetch('pages.json')
            let data = await res.json()
            console.log(data)
            
            this.pages = data
        }
    }
}
</script>