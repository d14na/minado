<template>
    <div class="app">
        <AppHeader fixed>
            <SidebarToggler class="d-lg-none" display="md" mobile />

            <b-link class="navbar-brand" to="#">
                <img class="navbar-brand-full" src="img/brand/logo.svg" width="89" height="25" alt="CoreUI Logo">
                <img class="navbar-brand-minimized" src="img/brand/sygnet.svg" width="30" height="30" alt="CoreUI Logo">
            </b-link>

            <SidebarToggler class="d-md-down-none" display="lg" />

            <b-navbar-nav class="d-md-down-none">
                <!-- <b-nav-item class="px-3" to="/dashboard">Dashboard</b-nav-item>
                <b-nav-item class="px-3" to="/ministo" exact>Ministo</b-nav-item> -->
                <div class="tagline">
                    Welcome to Minado :. POW Token Mining Community
                </div>
            </b-navbar-nav>

            <b-navbar-nav class="ml-auto">
                <!-- spacer -->
            </b-navbar-nav>

            <!-- <AsideToggler class="d-none d-lg-block" /> -->
            <!-- <AsideToggler class="d-lg-none" mobile /> -->
            <AsideToggler mobile />
        </AppHeader>

        <div class="app-body">
            <AppSidebar fixed>
                <SidebarHeader/>
                <SidebarForm/>
                <SidebarNav :navItems="nav"></SidebarNav>
                <SidebarFooter/>
                <SidebarMinimizer/>
            </AppSidebar>

            <main class="main">
                <Breadcrumb :list="list"/>
                <div class="container-fluid">
                    <router-view></router-view>
                </div>
            </main>

            <AppAside fixed>
                <!--aside-->
                <DefaultAside/>
            </AppAside>
        </div>

        <!--footer-->
        <TheFooter>
            <div>
                <a href="https://minado.network" target="_blank">Minado</a>
                <span class="ml-1">&copy; 2019 <a href="https://d14na.org" target="_blank">D14na MDAO</a>.</span>
            </div>

            <div class="ml-auto">
                <span class="mr-1">Built with</span>
                <a href="https://coreui.io" target="_blank">CoreUI for Vue</a>
            </div>
        </TheFooter>
    </div>
</template>

<script>
import nav from '@/_nav'

import {
    Header as AppHeader,
    SidebarToggler,
    Sidebar as AppSidebar,
    SidebarFooter,
    SidebarForm,
    SidebarHeader,
    SidebarMinimizer,
    SidebarNav,
    Aside as AppAside,
    AsideToggler,
    Footer as TheFooter,
    Breadcrumb
} from '@coreui/vue'

import DefaultAside from './DefaultAside'

export default {
    name: 'DefaultContainer',
    components: {
        AsideToggler,
        AppHeader,
        AppSidebar,
        AppAside,
        TheFooter,
        Breadcrumb,
        DefaultAside,
        SidebarForm,
        SidebarFooter,
        SidebarToggler,
        SidebarHeader,
        SidebarNav,
        SidebarMinimizer
    },
    data () {
        return {
            nav: nav.items
        }
    },
    computed: {
        name () {
            return this.$route.name
        },
        list () {
            return this.$route.matched.filter((route) => route.name || route.meta.label )
        }
    },
    mounted: async function () {
        /* Minimize the sidebar at start. */
        // const isMinimized = document.body.classList.toggle('sidebar-minimized')
        // this.$emit('cui-sidebar-minimize', isMinimized)

        /* Minimize the brand at start. */
        // document.body.classList.toggle('brand-minimized')
    }
}
</script>

<style>
.tagline {
    font-style: italic;
    margin-left: 10px;
}
</style>
