<template>
    <div class="flex flex-col gap-6">
        <p class="mainHeading">Выход из аккаунта</p>
        <button @click="logout" class="cursor-pointer px-10 py-1.5 bg-[#E6F5EE] rounded-full text-center w-fit">Выйти</button>
    </div>
</template>

<script setup>
/* проверка роли и создание сообщений */
const userStore = useUserStore()
const { id:userId, role, logout } = useUserStore()
const { showMessage } = useMessagesStore()


/* подключение БД и роутера */
const supabase = useSupabaseClient()
const router = useRouter()
</script>