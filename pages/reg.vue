<template>
    <div class="flex flex-col gap-8 grow justify-between">
        <NuxtLink to="/" class="flex items-center gap-2">
            <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl" />
            <p class="text-2xl">На главную</p>
        </NuxtLink>
        <FormKit @submit="regUser" type="form" :actions="false" messages-class="hidden" form-class="flex flex-col gap-6 items-center justify-center">
            <p class="mainHeading">Регистрация</p>
            <div class="flex flex-col gap-4 md:w-2/3 lg:w-1/2">
                <FormKit v-model="userForm.policy" validation="required|number" messages-class="text-[#E9556D]" type="text" placeholder="Полис" name="Полис" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
                <FormKit v-model="userForm.phone" validation="required|matches:/^[7-8]{1}-[0-9]{3}-[0-9]{3}-[0-9]{2}-[0-9]{2}$/" :validation-messages="{ matches: 'Номер телефона должен быть в формате 7/8-xxx-xxx-xx-xx', }" messages-class="text-[#E9556D]" type="tel" placeholder="x-xxx-xxx-xx-xx" name="Номер телефона" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
                <FormKit v-model="userForm.password" validation="required" messages-class="text-[#E9556D]" type="password" placeholder="······" name="Пароль" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
            </div>
            <button :disabled="isRegDisabled" :class="{ 'opacity-50 cursor-not-allowed': isRegDisabled }" type="submit" class="cursor-pointer px-10 py-1.5 bg-[#E6F5EE] rounded-full text-center">Зарегистрироватся</button>
        </FormKit>
        <p class="text-xl ml-auto w-fit">Уже есть аккаунт? <NuxtLink to="/auth" class="text-[#263AA7]">Войти</NuxtLink></p>
    </div>
</template>

<script setup>
/* создание формы пользователя */
const userForm = ref({
    policy: '',
    phone: '',
    password: ''
})

/* создание сообщений */
const { showMessage } = useMessagesStore()


/* подключение БД и роутера */
const supabase = useSupabaseClient()
const router = useRouter()


/* регистрация пользователя */
const isRegDisabled = ref(false)
const regUser = async () => {
    isRegDisabled.value = true
    const { data: user, error: usersError } = await supabase
    .from('users')
    .select("*")
    .eq('phone', userForm.value.phone)
    .single()

    if (user) {
        userForm.value.phone = ""
        isRegDisabled.value = false
        return showMessage("Такой  логин уже используется!", false)
    } 

    const { data, error } = await supabase
    .from('users')
    .insert(userForm.value)
    .select()

    if (data) {
        console.log(data)
        showMessage('Успешная регистрация!', true)
        isRegDisabled.value = false
        router.push('/auth')
    } else {
        console.log(userForm.value)            
        isRegDisabled.value = false
        showMessage('Произошла ошибка!', false)
    }
}
</script>