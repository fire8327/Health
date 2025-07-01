<template>
    <div class="flex flex-col gap-6">
        <NuxtLink to="/" class="flex items-center gap-2">
            <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl" />
            <p class="text-2xl">На главную</p>
        </NuxtLink>
        <div class="grid grid-cols-2 gap-8 text-2xl">
            <div class="relative rounded-xl overflow-hidden transition-all duration-500 hover:scale-105 border border-black/10">
                <img src="/images/services/pediatrics.png" alt="pediatrics" class="w-full aspect-[5/1] object-cover blur-[5px] z-[0]">
                <NuxtLink to="/" class="absolute z-[1] text-center inset-0 flex items-center justify-center">Педиатрия</NuxtLink>
            </div>
            <div class="relative rounded-xl overflow-hidden transition-all duration-500 hover:scale-105 border border-black/10">
                <img src="/images/services/gynecology.png" alt="gynecology" class="w-full aspect-[5/1] object-cover blur-[5px] z-[0]">
                <NuxtLink to="/" class="absolute z-[1] text-center inset-0 flex items-center justify-center">Гинекология</NuxtLink>
            </div>
            <div class="relative rounded-xl overflow-hidden transition-all duration-500 hover:scale-105 border border-black/10">
                <img src="/images/services/cardiology.png" alt="cardiology" class="w-full aspect-[5/1] object-cover blur-[5px] z-[0]">
                <NuxtLink to="/" class="absolute z-[1] text-center inset-0 flex items-center justify-center">Кардиология</NuxtLink>
            </div>
            <div class="relative rounded-xl overflow-hidden transition-all duration-500 hover:scale-105 border border-black/10">
                <img src="/images/services/surgery.png" alt="surgery" class="w-full aspect-[5/1] object-cover blur-[5px] z-[0]">
                <NuxtLink to="/" class="absolute z-[1] text-center inset-0 flex items-center justify-center">Хирургия</NuxtLink>
            </div>
            <div class="relative rounded-xl overflow-hidden transition-all duration-500 hover:scale-105 border border-black/10">
                <img src="/images/services/neurology.png" alt="neurology" class="w-full aspect-[5/1] object-cover blur-[5px] z-[0]">
                <NuxtLink to="/" class="absolute z-[1] text-center inset-0 flex items-center justify-center">Неврология</NuxtLink>
            </div>
            <div class="relative rounded-xl overflow-hidden transition-all duration-500 hover:scale-105 border border-black/10">
                <img src="/images/services/dermatology.png" alt="dermatology" class="w-full aspect-[5/1] object-cover blur-[5px] z-[0]">
                <NuxtLink to="/" class="absolute z-[1] text-center inset-0 flex items-center justify-center">Дерматология</NuxtLink>
            </div>
            <div class="relative rounded-xl overflow-hidden transition-all duration-500 hover:scale-105 border border-black/10">
                <img src="/images/services/nephrology.png" alt="nephrology" class="w-full aspect-[5/1] object-cover blur-[5px] z-[0]">
                <NuxtLink to="/" class="absolute z-[1] text-center inset-0 flex items-center justify-center">Нефрология</NuxtLink>
            </div>
            <div class="relative rounded-xl overflow-hidden transition-all duration-500 hover:scale-105 border border-black/10">
                <img src="/images/services/gastroenterology.png" alt="gastroenterology" class="w-full aspect-[5/1] object-cover blur-[5px] z-[0]">
                <NuxtLink to="/" class="absolute z-[1] text-center inset-0 flex items-center justify-center">Гастроэнтерология</NuxtLink>
            </div>
        </div>
    </div>
</template>

<script setup>

</script>