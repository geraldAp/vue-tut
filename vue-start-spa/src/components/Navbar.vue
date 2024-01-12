<template>
    <nav class="navbar navbar-expand-lg" :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">My Vue</a>
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <!-- <li class="nav-item">
            <a href="#" aria-current="page" class="nav-link">{{links[0]}}</a>
          </li>  v-for for thr for in loop -->
                <li v-for="(page, index) in pages" class="nav-item" :key="index">
                    <!-- v-bind to tell this we will be bind a value to this attribute is a js expression  but we can just use : then followed by the attribute -->
                    <!-- .prevent to stop it from going to the link in the href  -->
                    <navbar-link :page="page" :isActive="activePage == index" @click.prevent="navLinkClick(index)" />
                </li>
            </ul>
            <form action="" class="d-flex">
                <button class="btn btn-primary" @click.prevent="changeTheme()">
                    toggle Navbar
                </button>
            </form>
        </div>
    </nav>
</template>


<script>
import NavbarLink from './NavbarLink.vue';

export default {
    components: {
        NavbarLink
    },
    props: ['pages', 'activePage', 'navLinkClick'],
    data() {
        return {
            theme: "light",
        };
    },

    // for functions
    methods: {
        changeTheme() {
            let theme = "light";
            if (this.theme == "light") {
                theme = "dark";
            } else {
                theme = "light";
            }

            this.theme = theme;
        },
    },


}

</script>