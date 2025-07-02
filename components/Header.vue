<template>
    <header class="w-full grid-container py-4 font-light">
        <div class="flex flex-col gap-5">
            <div class="flex items-center justify-between">
                <NuxtLink to="/" class="text-3xl">Здоровье++</NuxtLink>
                <NuxtLink to="/auth" class="text-3xl flex">
                    <Icon name="ix:user-profile"/>
                </NuxtLink>
            </div>
            <div class="flex items-center justify-between rounded-full bg-[#E6F5EE] text-center overflow-hidden">
                <NuxtLink to="/services" class="px-16 py-1.5 rounded-full mainLink">Услуги</NuxtLink>
                <NuxtLink to="/doctors" class="px-16 py-1.5 rounded-full mainLink">Врачи</NuxtLink>
                <NuxtLink to="/rec" class="px-16 py-1.5 rounded-full mainLink">Запись</NuxtLink>
                <NuxtLink to="/about" class="px-16 py-1.5 rounded-full mainLink">О клинике</NuxtLink>
                <NuxtLink to="/contacts" class="px-16 py-1.5 rounded-full mainLink">Контакты</NuxtLink>
            </div>
        </div>
        <button type="button" @click="messageTitle = null" class="fixed top-10 right-10 z-[11] cursor-pointer flex items-center gap-2 px-6 py-2 text-lg rounded-xl w-fit font-medium font-mono bg-white border border-[#131313]/10 shadow-[0px_0px_13px_-7px_#131313]" :class="messageType ? ' text-[#131313]/80' : 'text-red-500'" v-if="messageTitle">
            <Icon class="text-3xl" name="material-symbols:close-small-rounded"/>
            <span>{{messageTitle}}</span>
        </button>
    </header>
</template>

<script setup>
/* создание сообщений */
const { messageTitle, messageType } = storeToRefs(useMessagesStore())


/* хранилище пользователей */
const userStore = useUserStore()
</script>