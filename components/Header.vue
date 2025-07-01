<template>
    <header class="w-full grid-container py-4 font-light">
        <div class="flex flex-col gap-5">
            <div class="flex items-center justify-between">
                <NuxtLink to="/" class="text-3xl">Здоровье++</NuxtLink>
                <NuxtLink to="/" class="text-3xl">
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
    </header>
</template>

<script setup>

</script>