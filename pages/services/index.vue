<template>
    <div class="flex flex-col gap-6">
        <NuxtLink to="/" class="flex items-center gap-2">
            <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl" />
            <p class="text-2xl">На главную</p>
        </NuxtLink>
        <div class="grid grid-cols-2 gap-8 text-2xl">
            <div v-for="speciality in specialities" class="relative rounded-xl overflow-hidden transition-all duration-500 hover:scale-105 border border-black/10">
                <img :src="`/images/services/${speciality.id}.png`" :alt="speciality.name" class="w-full aspect-[5/1] object-cover blur-[5px] z-[0]">
                <NuxtLink :to="`/services/service-${speciality.id}`" class="absolute z-[1] text-center inset-0 flex items-center justify-center">{{ speciality.name }}</NuxtLink>
            </div>
        </div>
    </div>
</template>

<script setup>
/* подключение БД, сообщений и пользователя*/
const supabase = useSupabaseClient()


/* получение специальностей */
const specialities = ref([])
const loadSpecialities = async () => {
    const { data, error } = await supabase
        .from('specialty')
        .select('*')
    if (error) {
        console.error(error)
    }
    specialities.value = data
}


/* первоначальная загрузка */
onMounted(() => {
    loadSpecialities()
})
</script>