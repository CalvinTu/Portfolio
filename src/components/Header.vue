<script setup>
    import { ref } from 'vue';
    
    const isOpenMenu = ref(false);
    
    const FacebookLink = 'https://www.facebook.com/calvinadales/';
    const Instagram = 'https://www.instagram.com/clvntmlk/';
    
    const toggleMobileMenu = () => {
        isOpenMenu.value = !isOpenMenu.value;
    };
    </script>
    
    <template>
        <header class="bg-pearl white-900 text-black border-b border-pearl white-800">
            <nav class="mx-auto max-w-screen-xl px-4 py-3">
                <div class="flex flex-row items-center justify-between">
                    <router-link to="/" class="flex flex-col items-center">
                        <h1 class="font-bold text-2xl">My Portfolio</h1>
                        <p class="font-light text-sm">BSIT Student 4 B</p>
                    </router-link>
    
                    <div class="hidden lg:block">
                        <ul class="flex flex-row gap-6">
                            <li
                                :class="$route.name === 'home' ? 'text-cyan-400 font-medium' : 'text-gray-400 hover:text-cyan-400'">
                                <router-link to="/">Home</router-link>
                            </li>
                            <li
                                :class="$route.name === 'about' ? 'text-cyan-400 font-medium' : 'text-gray-400 hover:text-cyan-400'">
                                <router-link to="/about">About</router-link>
                            </li>
                            <li
                                :class="$route.name === 'projects' ? 'text-cyan-400 font-medium' : 'text-gray-400 hover:text-cyan-400'">
                                <router-link to="/projects">Projects</router-link>
                            </li>
                            <li
                                :class="$route.name === 'contact' ? 'text-cyan-400 font-medium' : 'text-gray-400 hover:text-cyan-400'">
                                <router-link to="/contact">Contact</router-link>
                            </li>
                        </ul>
                    </div>
    
                    <div class="hidden lg:block">
                        <ul class="flex flex-row items-center gap-3">
                            <a :href="FacebookLink" target="_blank" class="text-gray-400 hover:text-cyan-400">
                                <i class="fab fa-facebook"></i>
                            </a>
                            <a :href="Instagram" target="_blank" class="text-gray-400 hover:text-cyan-400">
                                <i class="fab fa-instagram"></i>
                            </a>
                        </ul>
                    </div>
    
                    <div @click="toggleMobileMenu"
                        class="cursor-pointer block lg:hidden text-gray-400 hover:text-cyan-400">
                        <i class="fas fa-bars"></i>
                    </div>
                </div>
    
                <div v-if="isOpenMenu" class="flex lg:hidden relative">
                    <div class="bg-gray-900 flex flex-col absolute top-14 left-0 w-full gap-4 shadow-lg p-4">
                        <router-link to="/"
                            :class="$route.name === 'home' ? 'text-cyan-400 font-medium' : 'text-gray-400 hover:text-cyan-400'">
                            Home
                        </router-link>
                        <router-link to="/about"
                            :class="$route.name === 'about' ? 'text-cyan-400 font-medium' : 'text-gray-400 hover:text-cyan-400'">
                            About
                        </router-link>
                        <router-link to="/projects"
                            :class="$route.name === 'projects' ? 'text-cyan-400 font-medium' : 'text-gray-400 hover:text-cyan-400'">
                            Projects
                        </router-link>
                        <router-link to="/contact"
                            :class="$route.name === 'contact' ? 'text-cyan-400 font-medium' : 'text-gray-400 hover:text-cyan-400'">
                            Contact
                        </router-link>
    
                        <ul class="flex flex-row items-center gap-3 mt-2">
                            <a :href="FacebookLink" target="_blank" class="text-gray-400 hover:text-cyan-400">
                                <i class="fab fa-facebook"></i>
                            </a>
                            <a :href="Instagram" target="_blank" class="text-gray-400 hover:text-cyan-400">
                                <i class="fab fa-instagram"></i>
                            </a>
                        </ul>
                    </div>
                </div>
            </nav>
        </header>
    </template>
    