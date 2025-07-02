<template>
    <div class="flex flex-col gap-8">
        <NuxtLink to="/" class="flex items-center gap-2">
            <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl" />
            <p class="text-2xl">На главную</p>
        </NuxtLink>
        <FormKit @submit="addRecord" v-if="userId" type="form" :actions="false" messages-class="hidden" form-class="flex flex-col gap-6 items-center justify-center">
            <p class="mainHeading">Записаться</p>
            <div class="flex flex-col gap-4 md:w-2/3 lg:w-1/2">
                <FormKit v-model="specialty" validation="required" messages-class="text-[#E9556D]" type="select" :options="specialties" placeholder="Специальность" name="Специальность" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
                <FormKit v-if="specialty" v-model="recordForm.doctor_id" validation="required" messages-class="text-[#E9556D]" type="select" :options="doctors" placeholder="Врач" name="Врач" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
                <FormKit v-model="recordForm.time" validation="required" messages-class="text-[#E9556D]" type="datetime-local" placeholder="Время" name="Время" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
            </div>
            <button :disabled="isRecDisabled" :class="{ 'opacity-50 cursor-not-allowed': isRecDisabled }" type="submit" class="cursor-pointer px-10 py-1.5 bg-[#E6F5EE] rounded-full text-center">Создать запись</button>
        </FormKit>
        <p v-else class="text-xl grow flex items-center justify-center">*Для записи необходимо авторизоваться</p>
    </div>
</template>

<script setup>
/* подключение БД, сообщений и пользователя*/
const supabase = useSupabaseClient()
const { showMessage } = useMessagesStore()
const { id:userId } = useUserStore()


/* форма записи */
const recordForm = ref({
    doctor_id: null,
    time: '',
    user_id: userId
})


/* получение специальностей */
const specialties = ref([])
const loadSpecialties = async () => {
    const { data, error } = await supabase
    .from('specialty')
    .select('id, name')

    if (error) {
        console.error(error)
    }

    specialties.value = data.map(i => ({ label: i.name, value: i.id }))
}


/* получение врачей */
const specialty = ref(null)
const doctors = ref([])
const loadDoctors = async (specialty) => {
    const { data, error } = await supabase
    .from('doctors')
    .select('*')
    .eq('specialty_id', specialty)

    if (error) {
        console.error(error)
    }

    doctors.value = data.map(i => ({ label: i.full_name, value: i.id }))
}

watch(specialty, () => {
    loadDoctors(specialty.value)
})


/* добавление записи */
const isRecDisabled = ref(false)
const addRecord = async () => {
    isRecDisabled.value = true
    recordForm.value.time = new Date(recordForm.value.time)

    const { data, error } = await supabase
    .from('records')
    .insert(recordForm.value)
    .select()

    if (data) {
        isRecDisabled.value = false
        showMessage('Запись успешно создана!', true)
    } else {
        showMessage('Произошла ошибка!', false)
    }
}


/* первоначальная загрузка */
onMounted(() => {
    loadSpecialties()
})
</script>