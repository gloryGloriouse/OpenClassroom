<template>
    <header class="sticky top-0 z-50 transition-all duration-300 ease-in-out bg-white shadow-md">
        <section :class="['w-full',isScrolled ? 'bg-gray-100/95 backdrop-blur shadow-md py-2' : 'bg-gray-100 py-4']">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex flex-col md:flex-row items-center justify-between gap-3 md:gap-6">
                    <div class="flex justify-between items-center w-full md:w-auto">
                        <a href="/" class="text-2xl font-bold text-green-500">
                            RestoGuru
                        </a>
                        <button class="md:hidden text-gray-700 hover:text-indigo-600"
                        aria-label="Toggle mobile Menu"
                        @click="isMobileMenuOpen = !isMobileMenuOpen">
                        <Icon icon="mdi:menu" class="w-6 h-6"/>
                        </button>
                    </div>
                    <!---Search bar-->
                    <form class="w-full md:flex-1 max-w-sm" role="search" aria-label="Site search">
                        <label class="relative w-full">
                            <input type="text" placeholder="Search ..." 
                            class="w-full px-3 py-2 text-xs border border-gray-300 rounded-full focus:outline-none 
                            focus:ring-2 focus:ring-indigo-400"/>
                            <button type="submit" class="absolute right-2 top-1/2 transform -translate-y-1/2
                            text-gray-500  hover:text-indigo-600 " aria-label="Search Button">
                                <Icon icon="mdi:magnify" class="w-4 h-4"/>
                            </button>
                        </label>
                    </form>
                    <!--Icons-->
                    <aside class="flex items-center justify-end space-x-4 w-full md:w-auto">
                        <button class="relative p-2 text-gray-700 hover:text-green-500" aria-label="Wish List">
                            <Icon icon="mdi:heart-outline" class="w-5 h-5"/>
                            <span class="absolute -top-1 -right-1 bg-green-400 text-white text-xs rounded-full 
                            flex h-5 w-5 items-center justify-center">3</span>
                        </button>
                        <button class="relative p-2 text-gray-700 hover:text-green-500" aria-label="Cart">
                            <Icon icon="mdi:cart-outline" class="w-5 h-5"/>
                            <span class="absolute -top-1 -right-1 bg-green-400 text-white text-xs rounded-full 
                            flex h-5 w-5 items-center justify-center">3</span>
                        </button>
                        <button class="relative p-2 text-gray-700 hover:text-green-500" aria-label="Account">
                            <Icon icon="mdi:account-circle-outline" class="w-5 h-5"/>
                            <span class="absolute -top-1 -right-1 bg-green-400 text-white text-xs rounded-full 
                            flex h-5 w-5 items-center justify-center">3</span>
                        </button>
                    </aside>
                </div>
            </div>
        </section>
        <!--NavBae Links-->
        <nav class="bg-green-950 " aria-label="Main navigator">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <ul class="hidden md:flex justify-center py-3 flex-wrap gap-x-6 text-sm font-meduim text-white">
                    <li v-for="item in navItems" :key="item.id" >
                        <a :href="item.link" class="text-white hover:text-green-300 transition-colors">
                                {{ item.name }}
                        </a>
                    </li>
                </ul>
                <section v-if="isMobileMenuOpen" class="md:hidden mt-4 bg-white rounded-lg shadow-md p-4 space-y-3 text-[#5D4037] text-center"
                aria-label="Mobile Menu">
                    <a v-for="item in navItems" :key="item.id" :href="item.link" class=" block hover:text-amber-600 text-sm font-meduim">
                        {{ item.name }}
                    </a>
                </section>
            </div>
        </nav>
    </header>
</template>

<script setup>
import {ref, onMounted, onUnmounted} from 'vue'
const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)
const navItems = ref([
    {id: 1, name: 'Home', link: '#home'},
    {id: 2, name: 'Products', link: '#products'},
    {id: 3, name: 'Category', link: '#category'},
    {id: 4, name: 'Offers', link: '#offers'},
    {id: 5, name: 'About', link: '#about'},
])
const handleScroll = () => {
    isScrolled.value = window.scrollY > 10
}
onMounted(() => {
    window.addEventListener('scroll', handleScroll)
})
onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
})
</script> 