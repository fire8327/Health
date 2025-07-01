<template>
    <div class="flex flex-col gap-8">
        <NuxtLink to="/" class="flex items-center gap-2">
            <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl" />
            <p class="text-2xl">На главную</p>
        </NuxtLink>
        <FormKit type="form" :actions="false" messages-class="hidden" form-class="flex flex-col gap-6 items-center justify-center">
            <p class="mainHeading">Записаться</p>
            <div class="flex flex-col gap-4 md:w-2/3 lg:w-1/2">
                <FormKit validation="required" messages-class="text-[#E9556D]" type="text" placeholder="Специальность" name="Специальность" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
                <FormKit validation="required" messages-class="text-[#E9556D]" type="text" placeholder="Врач" name="Врач" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
                <FormKit validation="required" messages-class="text-[#E9556D]" type="time" placeholder="Время" name="Время" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
            </div>
            <button type="submit" class="px-10 py-1.5 bg-[#E6F5EE] rounded-full text-center">Создать запись</button>
        </FormKit>
    </div>
</template>

<script setup>

</script>