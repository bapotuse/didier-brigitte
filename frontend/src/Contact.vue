<script setup>
import { onBeforeUnmount, onMounted, ref } from 'vue'
import { gsap } from 'gsap'

let gsapContext

const form = ref({
    name: '',
    email: '',
    subject: '',
    message: '',
})

const submitForm = () => {
    console.log('Form submitted:', form.value)
}

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
            .from('.js-info-card', { y: 40, autoAlpha: 0, stagger: 0.15, duration: 0.6 }, '-=0.4')
            .from('.js-form', { x: 90, autoAlpha: 0, scale: 0.95, duration: 0.8, ease: 'power4.out' }, '-=0.7')
            .from('.js-cta', { y: 16, scale: 0.95, autoAlpha: 0, duration: 0.55 }, '-=0.5')

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
    <section class="bg-[#fdf9f2] min-h-screen">
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

        <div class="px-4 md:px-10 mt-8">
            <div class="text-left text-7xl md:text-8xl ml-5">
                <h1 class="js-title-1 font-noto-serif font-bold tracking-tight text-[#1d1c18]">Prenons</h1>
                <h1 class="js-title-2 font-noto-serif italic mt-4 font-semibold tracking-tight text-[#c05e42]">contact</h1>
            </div>
        </div>

        <div class="flex flex-col gap-10 mt-16 px-4 md:px-10 md:flex-row md:gap-12 pb-20">
            <div class="flex flex-col gap-6 md:w-2/5">
                <div class="js-info-card bg-white p-8 rounded-[60px_0_60px_0] shadow-sm">
                    <h2 class="font-noto-serif italic text-3xl text-[#c05e42] mb-3">Adresse</h2>
                    <p class="font-manrope text-[#1d1c18] text-base leading-relaxed">
                        12 rue de la Pizza<br>
                        13001 Marseille<br>
                        France
                    </p>
                </div>
                <div class="js-info-card bg-white p-8 rounded-[60px_0_60px_0] shadow-sm">
                    <h2 class="font-noto-serif italic text-3xl text-[#c05e42] mb-3">Horaires</h2>
                    <p class="font-manrope text-[#1d1c18] text-base leading-relaxed">
                        Mardi – Samedi<br>
                        12h00 – 14h30 &nbsp;·&nbsp; 19h00 – 22h30<br>
                        <span class="text-[#1d1c18]/60">Fermé dimanche & lundi</span>
                    </p>
                </div>
                <div class="js-info-card bg-white p-8 rounded-[60px_0_60px_0] shadow-sm">
                    <h2 class="font-noto-serif italic text-3xl text-[#c05e42] mb-3">Téléphone</h2>
                    <p class="font-manrope text-[#1d1c18] text-base leading-relaxed">
                        04 91 00 00 00<br>
                        contact@didier-brigitte.fr
                    </p>
                </div>
            </div>

            <form @submit.prevent="submitForm" class="js-form md:w-3/5 bg-white p-10 rounded-[100px_0_100px_0] shadow-sm flex flex-col gap-6">
                <h2 class="font-noto-serif text-4xl text-[#1d1c18]">
                    Une question ?
                    <span class="font-noto-serif italic text-[#c05e42]">Écrivez-nous.</span>
                </h2>

                <div class="flex flex-col gap-2">
                    <label for="name" class="font-manrope text-xs tracking-widest text-[#1d1c18]/70">NOM</label>
                    <input
                        id="name"
                        v-model="form.name"
                        type="text"
                        required
                        class="font-manrope bg-transparent border-b border-[#1d1c18]/20 py-2 text-[#1d1c18] outline-none transition-colors focus:border-[#c05e42]"
                    >
                </div>

                <div class="flex flex-col gap-2">
                    <label for="email" class="font-manrope text-xs tracking-widest text-[#1d1c18]/70">EMAIL</label>
                    <input
                        id="email"
                        v-model="form.email"
                        type="email"
                        required
                        class="font-manrope bg-transparent border-b border-[#1d1c18]/20 py-2 text-[#1d1c18] outline-none transition-colors focus:border-[#c05e42]"
                    >
                </div>

                <div class="flex flex-col gap-2">
                    <label for="subject" class="font-manrope text-xs tracking-widest text-[#1d1c18]/70">SUJET</label>
                    <input
                        id="subject"
                        v-model="form.subject"
                        type="text"
                        required
                        class="font-manrope bg-transparent border-b border-[#1d1c18]/20 py-2 text-[#1d1c18] outline-none transition-colors focus:border-[#c05e42]"
                    >
                </div>

                <div class="flex flex-col gap-2">
                    <label for="message" class="font-manrope text-xs tracking-widest text-[#1d1c18]/70">MESSAGE</label>
                    <textarea
                        id="message"
                        v-model="form.message"
                        rows="5"
                        required
                        class="font-manrope bg-transparent border-b border-[#1d1c18]/20 py-2 text-[#1d1c18] outline-none transition-colors focus:border-[#c05e42] resize-none"
                    ></textarea>
                </div>

                <button
                    type="submit"
                    class="js-cta self-start mt-4 font-manrope text-sm tracking-widest text-white font-light bg-[#c05e42] px-10 py-5 rounded-lg hover:cursor-pointer hover:bg-[#ac5037]"
                >
                    ENVOYER LE MESSAGE
                </button>
            </form>
        </div>
    </section>
</template>
