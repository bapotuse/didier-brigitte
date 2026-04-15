<script setup>
import { onBeforeUnmount, onMounted } from 'vue'
import { gsap } from 'gsap'

let gsapContext

onMounted(() => {
    gsapContext = gsap.context(() => {
        const introTimeline = gsap.timeline({ defaults: { ease: 'power3.out' } })

        gsap.set('.js-nav-link', { opacity: 1, visibility: 'visible' })

        introTimeline
            .from('.js-logo', { y: -24, autoAlpha: 0, duration: 0.7 })
            .fromTo(
                '.js-nav-link',
                { y: -14, opacity: 0 },
                { y: 0, opacity: 1, stagger: 0.12, duration: 0.45, clearProps: 'opacity,transform' },
                '-=0.4'
            )
            .from('.js-title-1', { x: -70, autoAlpha: 0, duration: 0.8 }, '-=0.1')
            .from('.js-title-2', { x: -45, autoAlpha: 0, duration: 0.8 }, '-=0.55')
            .from('.js-cta', { y: 16, scale: 0.95, autoAlpha: 0, duration: 0.55 }, '-=0.45')
            .from('.js-hero-image', { x: 90, autoAlpha: 0, scale: 0.92, duration: 0.80, ease: 'power4.out' }, '-=0.95')

        gsap.to('.js-cta', {
            boxShadow: '0 14px 26px rgba(192, 94, 66, 0.35)',
            duration: 1.8,
            repeat: -1,
            yoyo: true,
            ease: 'sine.inOut',
        })
    })
})

onBeforeUnmount(() => {
    gsapContext?.revert()
})
</script>

<template>
    <section class="bg-[#fdf9f2]">
        <nav class="relative flex flex-col gap-4 p-4 text-2xl md:flex-row md:items-center md:justify-between md:text-2xl">
            <router-link to="/" class="js-logo ml-5 tracking-tight no-underline text-[#c05e42]">
                <img class="w-1/6" src="../src/img/logo.png" alt="">
            </router-link>
            <div class="z-10 flex flex-col items-center gap-3 text-sm md:absolute md:left-1/2 md:flex-row md:gap-8 md:-translate-x-1/2">
                <router-link to="/click-and-collect" class="js-nav-link relative text-black font-manrope no-underline transition-opacity hover:opacity-70 after:absolute after:left-0 after:-bottom-1 after:h-0.5 after:w-0 after:bg-[#c05e42] after:transition-all after:duration-300 hover:after:w-full">
                    CLICK AND COLLECT
                </router-link>
                <router-link to="/contact" class="js-nav-link relative text-black font-manrope no-underline transition-opacity hover:opacity-70 after:absolute after:left-0 after:-bottom-1 after:h-0.5 after:w-0 after:bg-[#c05e42] after:transition-all after:duration-300 hover:after:w-full">
                    CONTACT
                </router-link>
            </div>
        </nav>
        <div class="flex flex-col gap-6 md:flex-row md:px-4 md:items-center md:justify-between">
            <div class="text-left text-8xl ml-5 md:w-1/2 md:self-center">
                <h1 class="js-title-1 font-noto-serif font-bold tracking-tight text-[#1d1c18]">Meilleure pizzeria de</h1>
                <h1 class="js-title-2 font-noto-serif italic mt-4 font-semibold tracking-tight text-[#c05e42]">Marseille</h1>
                <button class="js-cta font-manrope text-sm tracking-widest text-white font-light bg-[#c05e42] px-10 py-5 rounded-lg hover:cursor-pointer hover:bg-[#ac5037]">VOIR LE MENU</button>
            </div>
            <img class="js-hero-image self-end md:w-1/2 rounded-[100px_0_100px_0] shadow-fuchsia-500" src="../src/img/pizza.jpg" alt="Pizza">
        </div>
    </section>
    <div>

    </div>
</template>