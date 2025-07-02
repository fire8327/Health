<template>
    <div class="flex flex-col gap-10">
        <NuxtLink to="/" class="flex items-center gap-2">
            <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl" />
            <p class="text-2xl">На главную</p>
        </NuxtLink>
        <p class="text-2xl">
            Педиатрия в Казани: услуги квалифицированного педиатра в нашей клинике
            Врач-педиатр в Казани – это специалист, который занимается диагностикой, терапией заболеваний у
            несовершеннолетних пациентов, осуществляет профилактические меры для предотвращения заболеваний в детском
            возрасте.
        </p>
        <div class="grid grid-cols-3 gap-10">
            <div class="flex flex-col gap-4 p-4 rounded-xl bg-[#F4EFE6]" v-for="doctor in doctors">
                <div class="flex items-center gap-4">
                    <img :src="`/images/doctors/${doctor.avatar}`" :alt="doctor.full_name" class="w-20 rounded-full aspect-square object-cover object-center shadow-2xl">
                    <p class="text-2xl">{{ doctor.full_name }}</p>
                </div>
                <p>{{ doctor.position }}</p>
                <div class="flex items-center justify-between mt-auto">
                    <p class="text-xl">Стаж {{ doctor.experience }} лет</p>
                    <div class="flex items-center gap-1">
                        <Icon class="text-2xl text-amber-400" name="material-symbols:star" v-for="i in doctor.rating" />
                    </div>
                </div>
            </div>
        </div>
        <div class="relative rounded-xl overflow-hidden">
            <table class="text-xl w-full text-center">
                <tr class="bg-[#F4EFE6] odd:bg-[#E6F5EE] font-normal">
                    <td class="px-10 py-6">Код услуги</td>
                    <td class="px-10 py-6">Наименование услуги</td>
                    <td class="px-10 py-6">Цена услуги (в руб.)</td>
                </tr>
                <tr class="bg-[#F4EFE6] odd:bg-[#E6F5EE]" v-for="service in services">
                    <td class="px-10 py-6">{{ service.code }}</td>
                    <td class="px-10 py-6">{{ service.name }}</td>
                    <td class="px-10 py-6">{{ service.price.toLocaleString() }}</td>
                </tr>
            </table>
        </div>
        <NuxtLink to="/rec" class="px-10 py-1.5 bg-[#E6F5EE] rounded-full text-center w-fit mx-auto">Записаться</NuxtLink>
    </div>
</template>

<script setup>
/* подключение БД и роута*/
const supabase = useSupabaseClient()
const route = useRoute()


/* получение услуг */
const services = ref([])
const loadServices = async () => {
    const { data, error } = await supabase
    .from('services')
    .select('*')
    .eq('specialty_id', route.params.id)

    if (error) {
        console.error(error)
    }

    services.value = data
}


/* получение врачей */
const doctors = ref([])
const loadDoctors = async () => {
    const { data, error } = await supabase
    .from('doctors')
    .select('*')
    .eq('specialty_id', route.params.id)

    if (error) {
        console.error(error)
    }

    doctors.value = data
}


/* первоначальная загрузка */
onMounted(() => {
    loadServices()
    loadDoctors()
})
</script>