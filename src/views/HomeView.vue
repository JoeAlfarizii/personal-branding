<template>
    <div
        class="mx-auto min-h-screen max-w-screen-xl px-6 py-12 font-sans md:px-12 md:py-16 lg:py-0"
    >
        <div class="lg:flex lg:justify-between lg:gap-4">
            <Navbar />
            <main id="content" class="pt-24 lg:w-[52%] lg:py-24">
                <About />
                <Experiences />
                <Projects />
                <Footer />
            </main>
        </div>
    </div>
</template>

<script setup>
    import Navbar from '@/components/Navbar.vue'
    import About from '@/components/About.vue'
    import Projects from '@/components/Projects.vue'
    import Experiences from '@/components/Experiences.vue'
    import Footer from '@/components/Footer.vue'
</script>
