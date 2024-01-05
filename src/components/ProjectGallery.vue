<template>
    <div class="">
        <div class="flex flex-wrap lg:flex-nowrap items-center justify-between gap-4 lg:gap-1 mb-8 md:mb-12">
            <div class="flex flex-col gap-2">
                <h2 class="text-2xl font-bold text-gray-800 lg:text-3xl">Projects</h2>

                <p class="text-gray-500 text-lg">
                    This is my latest Projects
                </p>
            </div>

            <router-link to="/projects"
                class="inline-block rounded-lg border bg-white px-4 py-2 text-center text-sm font-semibold text-gray-500 outline-none 
                ring-indigo-300 transition duration-100 hover:bg-gray-100 focus-visible:ring active:bg-gray-200 md:px-8 md:py-3 md:text-base">View More Projects
            </router-link>
        </div>
        
        <!-- Project Image Gallery -->
        <div class="grid grid-cols-2 gap-4 md:grid-cols-6  ">
            <!-- image - start -->
            <router-link to="/projects" href="#" class="group relative flex h-48 items-end overflow-hidden rounded-lg bg-gray-100 shadow-lg md:h-80">
                <img src="../assets/OIP.jpg"
                    loading="lazy" alt="Photo by Minh Pham"
                    class="absolute inset-0 h-full w-full object-cover object-center transition duration-200 group-hover:scale-110" />

                <div
                    class="pointer-events-none absolute inset-0 bg-gradient-to-t from-gray-800 via-transparent to-transparent opacity-50">
                </div>

                <span class="relative ml-4 mb-3 inline-block text-sm text-white md:ml-5 md:text-lg">Click here to play</span>
            </router-link>
            <!-- image - end -->
        </div>
    </div>
</template>