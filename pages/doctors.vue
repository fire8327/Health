<template>
    <div class="flex flex-col gap-8">
        <NuxtLink to="/" class="flex items-center gap-2">
            <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl" />
            <p class="text-2xl">На главную</p>
        </NuxtLink>
        <div class="flex flex-col gap-4">
            <p class="mainHeading">Педиатрия</p>
            <div class="grid grid-cols-3 gap-10">
                <div class="flex flex-col gap-4 p-4 rounded-xl bg-[#F4EFE6]">
                    <div class="flex items-center gap-4">
                        <img src="/images/index/1.png" alt="" class="rounded-full shadow-2xl">
                        <p class="text-2xl">Закарьяева Анна Альбертовна</p>
                    </div>
                    <p>
                        Заведующая педиатрического 
                        отделения, врач-педиатр, 
                        кандидат медицинских наук
                    </p>
                    <div class="flex items-center justify-between">
                        <p class="text-xl">Стаж 10 лет</p>
                        <div class="flex items-center gap-1">
                            <Icon class="text-2xl text-amber-400" name="material-symbols:star" v-for="i in 5" />
                        </div>
                    </div>
                </div>
                <div class="flex flex-col gap-4 p-4 rounded-xl bg-[#F4EFE6]">
                    <div class="flex items-center gap-4">
                        <img src="/images/index/1.png" alt="" class="rounded-full shadow-2xl">
                        <p class="text-2xl">Закарьяева Анна Альбертовна</p>
                    </div>
                    <p>
                        Заведующая педиатрического 
                        отделения, врач-педиатр, 
                        кандидат медицинских наук
                    </p>
                    <div class="flex items-center justify-between">
                        <p class="text-xl">Стаж 10 лет</p>
                        <div class="flex items-center gap-1">
                            <Icon class="text-2xl text-amber-400" name="material-symbols:star" v-for="i in 5" />
                        </div>
                    </div>
                </div>
                <div class="flex flex-col gap-4 p-4 rounded-xl bg-[#F4EFE6]">
                    <div class="flex items-center gap-4">
                        <img src="/images/index/1.png" alt="" class="rounded-full shadow-2xl">
                        <p class="text-2xl">Закарьяева Анна Альбертовна</p>
                    </div>
                    <p>
                        Заведующая педиатрического 
                        отделения, врач-педиатр, 
                        кандидат медицинских наук
                    </p>
                    <div class="flex items-center justify-between">
                        <p class="text-xl">Стаж 10 лет</p>
                        <div class="flex items-center gap-1">
                            <Icon class="text-2xl text-amber-400" name="material-symbols:star" v-for="i in 5" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>

</script>