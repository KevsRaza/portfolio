<template>
    <section class="relative py-20 overflow-hidden" id="projects">
        <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Header -->
            <div class="text-center mb-16" data-aos="fade-up">
                <h2 class="text-4xl md:text-5xl font-bold text-white mb-4">
                    My <span class="text-transparent bg-clip-text bg-linear-to-r from-blue-400 to-cyan-400">
                        Projects
                    </span>
                </h2>
                <p class="text-blue-200 text-lg max-w-2xl mx-auto ">
                    A Collection of my recent work and creative solutions
                </p>
            </div>
            <!-- Projects -->

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Projet avec Swiper -->
                <div v-for="(project, index) in projects" :key="project.id"
                    class="group relative bg-linear-to-br from-gray-800/50 to-blue-900/30 rounded-3xl overflow-hidden border backdrop-blur-sm hover:border-blue-400/40 transition-all duration-500 hover:transform hover:-translate-y-2"
                    :class="project.bordColor" data-aos="fade-up" :data-aos-delay="(index + 1) * 100">
                    
                    <!-- Swiper Container -->
                    <div class="relative h-48 overflow-hidden">
                        <Swiper
                            v-if="project.images && project.images.length > 1"
                            :modules="[Navigation, Pagination, Autoplay]"
                            :navigation="{
                                nextEl: `.swiper-button-next-${project.id}`,
                                prevEl: `.swiper-button-prev-${project.id}`
                            }"
                            :pagination="{
                                clickable: true,
                                el: `.swiper-pagination-${project.id}`,
                                bulletClass: 'swiper-pagination-bullet-custom',
                                bulletActiveClass: 'swiper-pagination-bullet-custom-active'
                            }"
                            :loop="true"
                            :autoplay="{
                                delay: 3000,
                                disableOnInteraction: false
                            }"
                            class="h-full"
                        >
                            <SwiperSlide v-for="(image, imgIndex) in project.images" :key="imgIndex">
                                <img 
                                    :src="image" 
                                    :alt="`${project.title} - Image ${imgIndex + 1}`"
                                    :class="[
                                        'w-full h-48 transition-transform duration-500',
                                        project.id === 3 
                                            ? 'object-contain bg-gray-900 group-hover:scale-105'
                                            : (project.id === 1 && imgIndex === 2)
                                                ? 'object-contain bg-gray-900 group-hover:scale-105'
                                                : 'object-cover group-hover:scale-110'
                                    ]"
                                />
                                <!-- Overlay Gradient-->
                                <div class="absolute inset-0 bg-linear-to-t from-gray-900/80 via-gray-900/20 to-transparent"></div>
                            </SwiperSlide>
                        </Swiper>

                        <!-- Simple Image -->
                        <div v-else class="h-full">
                            <img 
                                :src="project.image" 
                                :alt="project.title"
                                class="w-full h-48 object-cover transition-transform duration-500 group-hover:scale-110"
                            />
                            <div class="absolute inset-0 bg-linear-to-t from-gray-900/80 via-gray-900/20 to-transparent"></div>
                        </div>

                        <!-- Badge  -->
                        <div class="absolute top-4 right-4 z-20">
                            <span class="px-3 py-1 text-white text-xs rounded-full font-semibold"
                                :class="project.badgeColor">
                                {{ project.category }}
                            </span>
                        </div>

                        <!-- Swiper Navigation -->
                        <template v-if="project.images && project.images.length > 1">
                            <!-- Previous Button -->
                            <button 
                                :class="`swiper-button-prev-${project.id} absolute left-2 top-1/2 transform -translate-y-1/2 z-20 w-8 h-8 flex items-center justify-center bg-black/50 rounded-full text-white hover:bg-blue-400 transition-colors opacity-0 group-hover:opacity-100`"
                            >
                                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"/>
                                </svg>
                            </button>
                            
                            <!-- Next Button -->
                            <button 
                                :class="`swiper-button-next-${project.id} absolute right-2 top-1/2 transform -translate-y-1/2 z-20 w-8 h-8 flex items-center justify-center bg-black/50 rounded-full text-white hover:bg-blue-400 transition-colors opacity-0 group-hover:opacity-100`"
                            >
                                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/>
                                </svg>
                            </button>

                            <!-- Pagination -->
                            <div :class="`swiper-pagination-${project.id} absolute bottom-2 left-1/2 transform -translate-x-1/2 z-20 flex space-x-1`"></div>
                        </template>
                    </div>

                    <!-- Content -->
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-white group-hover:text-blue-400 transition-colors duration-300">
                            {{ project.title }}
                        </h3>
                        <p class="text-gray-300 text-sm leading-relaxed mb-4">
                            {{ project.desc }}
                        </p>
                        
                        <!-- Technos -->
                        <div class="flex flex-wrap gap-2 mb-4">
                            <span v-for="tech in project.techno" :key="tech.name" class="px-2 py-1 border rounded text-xs"
                                :class="tech.class">
                                {{ tech.name }}
                            </span>
                        </div>
                        
                        <!-- Project Links -->
                        <div class="flex gap-3">
                            <a v-for="link in project.links" :key="link.name" 
                                :href="link.url" 
                                :class="link.class"
                                target="_blank"
                                class="flex items-center gap-2 transition-colors duration-300 text-sm font-medium text-gray-400 hover:text-[#CA3E47]">
                                <component :is="link.icon" class="w-4 h-4" />
                                {{ link.name }}
                            </a>
                        </div>
                    </div>
                </div>
            </div>

            <!-- CTA Section -->
            <div class="text-center mt-16" data-aos="fade-up">
                <div class="inline-flex flex-col sm:flex-row gap-4 items-center">
                    <!-- <button class="px-8 py-4 rounded-xl bg-linear-to-r from-blue-500 to-cyan-500 text-white font-semibold hover:shadow-lg hover:shadow-blue-500/25 transition-all duration-300 hover:scale-105 flex items-center">
                        View All Projects
                        <ArrowRightIcon class="w-5 h-5 ml-2"/>
                    </button> -->
                    <a href="#contact"
                        class="px-8 py-4 rounded-xl border-2 border-blue-400 text-blue-400 font-semibold hover:bg-blue-400/10 transition-all duration-300 flex items-center">
                        <ChatBubbleLeftRightIcon class="w-5 h-5 mr-2" />
                        Discuss Project
                    </a>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { CodeBracketIcon, EyeIcon, ArrowRightIcon, ChatBubbleLeftRightIcon } from '@heroicons/vue/16/solid';
import { Navigation, Pagination, Autoplay } from 'swiper/modules';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { ref } from 'vue';

import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import 'swiper/css/autoplay';

const projects = ref([
    {
        id: 1,
        title: "Schulmanager",
        desc: 'German administrative management platform built with Laravel & Livewire, enabling the management of students, companies, schools, folders, and forms with search, sorting, pagination, and file uploads.',
        images: [
                '../project1-1.png',
                '../project1-2.png',
                '../project1-3.png',
            ],
        category: 'Full-Stack',
        bordColor: 'border-blue-500/20',
        badgeColor: 'bg-blue-500',
        techno: [
            {
                name: "Laravel",
                class: 'bg-blue-500/20 border-blue-400/30 text-blue-200'
            },
            {
                name: "Bootstrap",
                class: 'bg-cyan-500/20 border-cyan-400/30 text-cyan-200'
            },
            {
                name: "MySQL",
                class: 'bg-blue-500/20 border-blue-400/30 text-blue-200'
            },
        ],
        links: [
            // {
            //     name: "Live Demo",
            //     url: "#",
            //     icon: EyeIcon,
            //     class: 'text-blue-400 hover:text-blue-300'
            // },
            {
                name: "Code",
                url: "https://github.com/KevsRaza/Schulmanager",
                icon: CodeBracketIcon,
                class: 'text-cyan-400 hover:text-cyan-300'
            },
        ]
    },
    {
        id: 2,
        title: "Portfolio",
        desc: 'I design and develop modern web applications and interactive bots, turning ideas into functional digital solutions with clean code and a focus on user experience.',
        image: '../public/project2.png',
        category: 'Portfolio',
        bordColor: 'border-blue-500/20',
        badgeColor: 'bg-blue-500',
        techno: [
            {
                name: "Vue.js",
                class: 'bg-cyan-500/20 border-cyan-400/30 text-cyan-200'
            },
            {
                name: "Tailwind CSS",
                class: 'bg-blue-500/20 border-blue-400/30 text-blue-200'
            },
            {
                name: "AOS",
                class: 'bg-cyan-500/20 border-cyan-400/30 text-cyan-200'
            },
        ],
        links: [
            {
                name: "Live Demo",
                url: "https://kevinraza-portfolio.vercel.app/",
                icon: EyeIcon,
                class: 'text-blue-400 hover:text-blue-300'
            },
            {
                name: "Code",
                url: "https://github.com/KevsRaza/portfolio",
                icon: CodeBracketIcon,
                class: 'text-cyan-400 hover:text-cyan-300'
            },
        ]
    },
    {
        id: 3,
        title: "Bot Discord (in progress...)",
        desc: 'This Discord bot offers moderation tools, fun games, and real-time notifications to enhance server management and user engagement.',
        images: [
                '../project3-1.png',
                '../project3-2.png',
                '../project3-3.png',
                '../project3-4.png',
            ],
        category: 'Bot',
        bordColor: 'border-blue-500/20',
        badgeColor: 'bg-blue-500',
        techno: [
            {
                name: "Python",
                class: 'bg-cyan-500/20 border-cyan-400/30 text-cyan-200'
            },
            {
                name: "Json",
                class: 'bg-blue-500/20 border-blue-400/30 text-blue-200'
            },
            {
                name: "Discord",
                class: 'bg-cyan-500/20 border-cyan-400/30 text-cyan-200'
            },
        ],
        links: [
            // {
            //     name: "Live Demo",
            //     url: "#",
            //     icon: EyeIcon,
            //     class: 'text-blue-400 hover:text-blue-300'
            // },
            {
                name: "Code",
                url: "https://github.com/KevsRaza/GuildGreeter",
                icon: CodeBracketIcon,
                class: 'text-cyan-400 hover:text-cyan-300'
            },
        ]
    }
])
</script>