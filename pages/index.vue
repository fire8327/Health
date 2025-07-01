<template>
    <div class="w-full rounded-xl overflow-hidden relative">
        <img src="/images/index/hero.png" alt="" class="w-full h-full object-cover aspect-video absolute z-[0] blur-[5px]">
        <div class="flex flex-col gap-16 w-full px-10 py-32 items-center text-center relative z-[1]">
            <p class="text-4xl max-w-[950px]">
                Мы - сеть многопрофильных клиник “Здоровье++”. <br>
                Мы помогаем на всех уровнях - от амбулаторного до 
                хирургического лечения.
            </p>
            <NuxtLink to="/" class="text-2xl px-4 py-1.5 rounded-full bg-[#E6F5EE] w-fit shadow-2xl">Записаться</NuxtLink>
        </div>
    </div>
    <div class="flex flex-col gap-6 items-center">
        <p class="mainHeading">Отзывы про нас</p>
        <div class="grid grid-cols-3 gap-10 w-full">
            <div class="flex flex-col gap-7 rounded-xl bg-[#F4EFE6] p-6 w-full">
                <div class="flex items-center justify-between">
                    <div class="flex items-center gap-5">
                        <img src="/images/index/1.png" alt="" class="rounded-full shadow-2xl">
                        <p class="text-3xl">Анна</p>
                    </div>
                    <div class="flex items-center gap-1">
                        <Icon class="text-2xl text-amber-400" name="material-symbols:star" v-for="i in 5"/>
                    </div>
                </div>
                <p class="text-xl">
                    Я обратилась в эту клинику к
                    эндокринологу, потому что она
                    была ближе всего к дому. Сама
                    клиника чистая, девушка на
                    ресепшн очень приятная, сама
                    консультация была очень
                    информативная...
                </p>
            </div>
            <div class="flex flex-col gap-7 rounded-xl bg-[#F4EFE6] p-6 w-full">
                <div class="flex items-center justify-between">
                    <div class="flex items-center gap-5">
                        <img src="/images/index/2.png" alt="" class="rounded-full shadow-2xl">
                        <p class="text-3xl">Ева</p>
                    </div>
                    <div class="flex items-center gap-1">
                        <Icon class="text-2xl text-amber-400" name="material-symbols:star" v-for="i in 5"/>
                    </div>
                </div>
                <p class="text-xl">
                    Записалась день в день на
                    эхокардиографию. Перезвонили
                    быстро и подтвердили запись.
                    👍 Приехала впервые. С порога
                    всё чисто, светло и красиво.
                    Это радует! Людей немного. И
                    я без проблем смогла найти...
                </p>
            </div>
            <div class="flex flex-col gap-7 rounded-xl bg-[#F4EFE6] p-6 w-full">
                <div class="flex items-center justify-between">
                    <div class="flex items-center gap-5">
                        <img src="/images/index/3.png" alt="" class="rounded-full shadow-2xl">
                        <p class="text-3xl">Дарья</p>
                    </div>
                    <div class="flex items-center gap-1">
                        <Icon class="text-2xl text-amber-400" name="material-symbols:star" v-for="i in 4"/>
                    </div>
                </div>
                <p class="text-xl">
                    Я обратился в данную клинику
                    из-за проблем с мочеполовой
                    системой, и был очень приятно
                    удивлён увидеть врача, который
                    разбирается в вопросе, и при
                    этом очень культурен. В
                    сравнении с бесплатной...
                </p>
            </div>
        </div>
    </div>
</template>

