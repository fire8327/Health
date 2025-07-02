<template>
    <NuxtLink to="/" class="flex items-center gap-2">
        <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl"/>
        <p class="text-2xl">На главную</p>
    </NuxtLink>
    <p></p>
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
    <div class="col-span-full w-full">
        <table class="text-xl w-full text-center">
            <tr class="bg-[#F4EFE6] odd:bg-[#E6F5EE] font-normal">
                <td class="px-10 py-6">Время</td>
                <td class="px-10 py-6">Врач</td>
                <td class="px-10 py-6">Наименование услуги</td>
                <td class="px-10 py-6">Цена услуги (в руб.)</td>
            </tr>
            <tr class="bg-[#F4EFE6] odd:bg-[#E6F5EE]">
                <td class="px-10 py-6">10:00</td>
                <td class="px-10 py-6">Закарьяева Анна Альбертовна</td>
                <td class="px-10 py-6">Педиатрия</td>
                <td class="px-10 py-6">2 500,00</td>
            </tr>
        </table>
    </div>
    <NuxtLink to="/rec" class="px-10 py-1.5 bg-[#E6F5EE] rounded-full text-center w-fit mx-auto">Записаться</NuxtLink>
</template>

<script setup>

</script>