<template>
    <header class="w-full grid-container py-4 font-light">
        <div class="flex flex-col gap-5">
            <div class="flex items-center justify-between">
                <NuxtLink to="/" class="text-3xl">Здоровье++</NuxtLink>
                <NuxtLink to="/" class="text-3xl">
                    <Icon name="ix:user-profile"/>
                </NuxtLink>
            </div>
            <div class="flex items-center justify-between px-16 py-1.5 rounded-full bg-[#E6F5EE] text-center">
                <NuxtLink to="/services">Услуги</NuxtLink>
                <NuxtLink to="/doctors">Врачи</NuxtLink>
                <NuxtLink to="/rec">Запись</NuxtLink>
                <NuxtLink to="/about">О клинике</NuxtLink>
                <NuxtLink to="/contacts">Контакты</NuxtLink>
            </div>
        </div>
    </header>
</template>

<script setup>

</script>