<template>
    <div class="flex flex-col gap-8">
        <div class="flex items-center justify-between">
            <NuxtLink to="/" class="flex items-center gap-2">
                <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl" />
                <p class="text-2xl">На главную</p>
            </NuxtLink>
            <FormKit v-model="specialty" messages-class="text-[#E9556D]" type="select" :options="specialties" placeholder="Специальность" name="Специальность" outer-class="w-[30%]" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
        </div>
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
    </div>
</template>

<script setup>
/* подключение БД и роута*/
const supabase = useSupabaseClient()


/* получение врачей */
const doctors = ref([])
const loadDoctors = async (specialty = null) => {
    let query = supabase
    .from('doctors')
    .select('*')

    if (specialty) {
        query = query.eq('specialty_id', specialty)
    }

    const { data, error } = await query

    if (error) {
        console.error(error)
    }

    doctors.value = data
}


/* получение специальностей */
const specialties = ref([])
const loadSpecialties = async () => {
    const { data, error } = await supabase
    .from('specialty')
    .select('id, name')

    if (error) {
        console.error(error)
    }

    specialties.value = [
    { label: 'Все', value: 'all' },
        ...data.map(i => ({ label: i.name, value: i.id }))
    ]
}


/* фильтрация */
const specialty = ref(null)
watch(specialty, () => {
    if (specialty.value && specialty.value !== 'all') {
        loadDoctors(specialty.value)
    } else {
        loadDoctors()
    }
})


/* первоначальная загрузка */
onMounted(() => {
    loadDoctors()
    loadSpecialties()
})
</script>