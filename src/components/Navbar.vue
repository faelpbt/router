<template>
    <header :class="{ 'scrolled-nav': scrolledNav }">

        <nav class="nav">

            <div>

                <router-link class="logo" to="/">
                    RAFAEL
                </router-link>

            </div>

            <ul v-if="!mobile" class="nav-list">

                <router-link class="nav-link" to="/">HOME</router-link>
                <router-link class="nav-link" to="/About">ABOUT</router-link>
                <router-link class="nav-link" to="/">SKILLS</router-link>

            </ul>

            <div class="nav-mobile">

                <i @click="toggleMobileNav" v-if="mobile" class="fas fa-bars icon" :class="{'icon-active': mobileNav }"></i>

            </div>

            <transition name="mobile-nav">

                <ul v-if="mobileNav" class="dropdown-list">

                    <router-link class="mobile-link" to="/">HOME</router-link>
                    <router-link class="mobile-link" to="/Cursos">ABOUT</router-link>
                    <router-link class="mobile-link" to="/">SKILLS</router-link>

                </ul>

            </transition> 

        </nav>

    </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return{
            scrolledNav: null,
            mobile: null,
            mobileNav: null,
            WindowWidth: null,
        };
    },
    created(){
        window.addEventListener('resize', this.checkScreen);
        this.checkScreen();
    },
    mounted(){
        window.addEventListener('scroll', this.updateScroll);
    },
    methods: {
        toggleMobileNav() {
            this.mobileNav = !this.mobileNav;
        },

        updateScroll(){
            const scrollPosition = window.scrollY;
            if (scrollPosition > 50) {
               this.scrolledNav = true;
               return;
            }
            this.scrolledNav = false;
        },

        checkScreen() {
            this.windowWidth = window.innerWidth;
            if (this.windowWidth <= 768) {
                this.mobile = true;
                return;
            }
            this.mobile = false;
            this.mobileNav = false;
            return;
        },
    },
}
</script>

<style lang="postcss" scoped>
header{
    @apply transition duration-500 ease-in bg-transparent w-full h-20 fixed z-50;
}
.nav{
    @apply transition duration-500 ease-in flex flex-row py-5 justify-between mx-5 xl:mx-10 2xl:mx-20 2xl:py-4;
}
.logo{
    @apply text-xl xl:text-2xl;
}
.nav-list{
    @apply hidden lg:block lg:py-2;
}
.nav-mobile{
    @apply lg:hidden;
}
.icon{
    @apply text-3xl text-black;
}
.icon-active{
    transform: rotate(180deg);
    transition: 1s linear all;
}
.nav-link{
    @apply lg:text-xl lg:px-3 xl:text-2xl xl:px-5 2xl:px-10;
}
.nav-button{
    @apply border rounded-full;
}
.start{
    color: #4E5FFF;
}
.mobile-link{
    @apply text-xl p-2;
}
.up{
    @apply font-bold;
}
.mobile-nav-enter-active,
.mobile-nav-leave-active{
    transition: 1s ease all;
}

.mobile-nav-enter-from,
.mobile-nav-leave-to{
    transform: translateX(-18rem);
}
.mobile-nav-enter-to{
    transform: translateX(0);
}
.dropdown-list{
    @apply lg:hidden;
    @apply pt-20 left-0 top-0 px-10 h-screen absolute flex flex-col w-full;
    max-width: 18rem;
    background: rgba(139, 158, 255, 0.26);
    box-shadow: 0px 4px 22px rgba(6, 17, 44, 0.22), inset -9px -52px 71px rgba(153, 194, 255, 0.15);
    backdrop-filter: blur(24px);
}
.scrolled-nav{
    background: rgba(139, 158, 255, 0.26);
    box-shadow: 0px 4px 22px rgba(6, 17, 44, 0.22), inset -9px -52px 71px rgba(153, 194, 255, 0.15);
    backdrop-filter: blur(24px);
}
</style>