<template>
    <div class="flex flex-col gap-6">
        <p class="mainHeading">Мои записи</p>
        <div class="grid grid-cols-4 gap-8">
            <div class="flex flex-col gap-4 p-4 rounded-xl bg-[#F4EFE6]" v-for="record in records">
                <button @click="deleteRecord(record.id)" class="cursor-pointer self-end">
                    <Icon name="material-symbols:delete-outline" class="text-3xl text-red-500"/>
                </button>
                <p>Время записи - {{ new Date(record.time).toLocaleString() }}</p>
                <p>Врач - {{ record.doctors.full_name }}</p>
            </div>
        </div>
    </div>
    <div class="flex flex-col gap-6">
        <p class="mainHeading">Выход из аккаунта</p>
        <button @click="logout" class="cursor-pointer px-10 py-1.5 bg-[#E6F5EE] rounded-full text-center w-fit">Выйти</button>
    </div>
</template>

<script setup>
/* проверка роли и создание сообщений */
const { id:userId, logout } = useUserStore()
const { showMessage } = useMessagesStore()


/* подключение БД и роутера */
const supabase = useSupabaseClient()


/* получение записей */
const records = ref([])
const loadRecords = async () => {
    const { data, error } = await supabase
    .from('records')
    .select('*, doctors(full_name)')
    .eq('user_id', userId)

    if (error) {
        console.error(error)
    }

    records.value = data
}


/* удаление записи */
const deleteRecord = async (id) => {
    const { error } = await supabase
    .from('records')
    .delete()
    .eq('id', id)

    if (error) {
        console.error(error)
        showMessage('Не удалось удалить запись', false)
    } else {
        showMessage('Запись удалена!', true)
    }

    loadRecords()
}


/* первоначальная загрузка */
onMounted(() => {
    loadRecords()
})
</script>