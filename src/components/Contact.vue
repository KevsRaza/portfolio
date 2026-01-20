<template>
    <section class="relative py-20 overflow-hidden" id="contact">
        <div class="relative z-10 max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center m-16" data-aos="fade-up">
                <h2 class="text-4xl md:text-5xl font-bold text-white mb-4">
                    Get In <span class="text-transparent bg-clip-text bg-linear-to-r from-blue-400 to-cyan-400">
                        Touch
                    </span>
                </h2>
                <p class="text-blue-200 text-lg">
                    Let's work together on your next project
                </p>
            </div>
            <div class="grid lg:grid-cols-2 gap-12">
                <div data-aos="fade-right">
                    <h3 class="text-2xl font-bold text-white mb-6">
                        Contact Information
                    </h3>
                    <div class="space-y-6">
                        <div class="flex items-center gap-4">
                            <EnvelopeIcon class="w-6 h-6 text-blue-400" />
                            <div>
                                <p class="text-white font-semibold">Email</p>
                                <p class="text-blue-200">krazafindralanto@gmail.com</p>
                            </div>
                        </div>
                        <div class="flex items-center gap-4">
                            <PhoneIcon class="w-6 h-6 text-blue-400" />
                            <div>
                                <p class="text-white font-semibold">Phone</p>
                                <p class="text-blue-200">+261 32 15 377 42</p>
                            </div>
                        </div>
                        <div class="flex items-center gap-4">
                            <MapPinIcon class="w-6 h-6 text-blue-400" />
                            <div>
                                <p class="text-white font-semibold">Location</p>
                                <p class="text-blue-200">Antananarivo, Madagascar</p>
                            </div>
                        </div>
                    </div>
                    <div class="mt-8">
                        <h4 class="text-lg font-bold text-white mb-4">Contact Me</h4>
                        <div class="flex gap-4">
                            <SocialIcon href="https://wa.me/261321537742" :icon="WhatsappIcon"
                                containerClass="bg-green-500/20 border-green-400/30 text-green-400 hover:bg-green-500/30" />

                            <SocialIcon href="https://m.me/kevsraza.30" :icon="MessengerIcon"
                                containerClass="bg-blue-500/20 border-blue-400/30 text-blue-400 hover:bg-blue-500/30" />

                            <SocialIcon href="https://linkedin.com/in/username" :icon="LinkedInIcon"
                                containerClass="bg-sky-500/20 border-sky-400/30 text-sky-400 hover:bg-sky-500/30" />

                            <SocialIcon href="https://t.me/kevsraza" :icon="TelegramIcon"
                                containerClass="bg-sky-500/20 border-sky-400/30 text-sky-400 hover:bg-sky-500/30" />
                        </div>
                    </div>

                </div>
                <div data-aos="fade-left">
                    <form class="space-y-6">
                        <div class="grid sm:grid-cols-2 gap-6">
                            <div>
                                <label class="text-white text-sm font-medium mb-2 block">
                                    Name
                                </label>
                                <input type="text"
                                    class="w-full bg-gray-800/50 border border-blue-500/30 rounded-xl px-4 py-3 text-white placeholder-blue-300 focus:border-blue-400 focus:outline-none transition-all">
                            </div>
                            <div>
                                <label class="text-white text-sm font-medium mb-2 block">
                                    Email
                                </label>
                                <input type="email"
                                    class="w-full bg-gray-800/50 border border-blue-500/30 rounded-xl px-4 py-3 text-white placeholder-blue-300 focus:border-blue-400 focus:outline-none transition-all">
                            </div>
                        </div>
                        <div>
                            <label class="text-white text-sm font-medium mb-2 block">
                                Subject
                            </label>
                            <input type="text"
                                class="w-full bg-gray-800/50 border border-blue-500/30 rounded-xl px-4 py-3 text-white placeholder-blue-300 focus:border-blue-400 focus:outline-none transition-all">
                        </div>
                        <div>
                            <label class="text-white text-sm font-medium mb-2 block">
                                Message
                            </label>
                            <textarea rows="4"
                                class="w-full bg-gray-800/50 border border-blue-500/30 rounded-xl px-4 py-3 text-white placeholder-blue-300 focus:border-blue-400 focus:outline-none transition-all"></textarea>
                        </div>
                        <button type="submit"
                            class="w-full bg-linear-to-r from-blue-500 to-cyan-500 text-white font-semibold py-3 rounded-xl hover:shadow-lg hover:shadow-blue-500/25 transition-all duration-300">Send
                            Message</button>
                    </form>
                </div>
            </div>
        </div>
    </section>
</template>
<script setup>
import SocialIcon from './SocialIcon.vue'

import WhatsappIcon from './icons/WhatsappIcon.vue'
import MessengerIcon from './icons/MessengerIcon.vue'
import LinkedInIcon from './icons/LinkedinIcon.vue'
import TelegramIcon from './icons/TelegramIcon.vue'

import {
    EnvelopeIcon,
    PhoneIcon,
    MapPinIcon
} from '@heroicons/vue/24/solid'


</script>