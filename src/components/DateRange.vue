<template>
    <div class="date-range">
        <p>{{ formattedRange }}</p>
    </div>
</template>

<script setup>
    import { computed } from 'vue'
    import { format, differenceInMonths, differenceInYears, parseISO } from 'date-fns'

    const props = defineProps({
        start: {
            type: String, // Format ISO: '2021-11-01'
            required: true,
        },
        end: {
            type: String, // Boleh null atau undefined
            default: null,
        },
    })

    const startDate = parseISO(props.start)
    const endDate = props.end ? parseISO(props.end) : new Date()

    const formattedStart = format(startDate, 'MMM yyyy')
    const formattedEnd = props.end ? format(endDate, 'MMM yyyy') : 'Present'

    // Hitung durasi
    const totalMonths = differenceInMonths(endDate, startDate)
    const years = Math.floor(totalMonths / 12)
    const months = totalMonths % 12

    const durationString = computed(() => {
        if (totalMonths <= 0) return 'Less than 1 mo'
        const parts = []
        if (years > 0) parts.push(`${years} yr${years > 1 ? 's' : ''}`)
        if (months > 0) parts.push(`${months} mo${months > 1 ? 's' : ''}`)
        return parts.join(' ')
    })

    const formattedRange = computed(() => {
        return `${formattedStart} — ${formattedEnd} (${durationString.value})`
    })
</script>

<style scoped>
    .date-range {
        font-family: sans-serif;
    }
</style>
