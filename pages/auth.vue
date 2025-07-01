<template>
    <div class="flex flex-col gap-8 grow justify-between">
        <NuxtLink to="/" class="flex items-center gap-2">
            <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl" />
            <p class="text-2xl">На главную</p>
        </NuxtLink>
        <FormKit type="form" :actions="false" messages-class="hidden" form-class="flex flex-col gap-6 items-center justify-center">
            <p class="mainHeading">Вход</p>
            <div class="flex flex-col gap-4 md:w-2/3 lg:w-1/2">
                <FormKit validation="required" messages-class="text-[#E9556D]" type="text" placeholder="Номер телефона" name="Номер телефона" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
                <FormKit validation="required" messages-class="text-[#E9556D]" type="password" placeholder="······" name="Пароль" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
            </div>
            <button type="submit" class="px-10 py-1.5 bg-[#E6F5EE] rounded-full text-center">Войти</button>
        </FormKit>
        <p class="text-xl ml-auto w-fit">Ещё нет аккаунта? <NuxtLink to="/reg" class="text-[#263AA7]">Зарегистрироваться</NuxtLink></p>
    </div>
</template>

<script setup>

</script>