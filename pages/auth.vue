<template>
    <div class="flex flex-col gap-8 grow justify-between">
        <NuxtLink to="/" class="flex items-center gap-2">
            <Icon name="material-symbols:keyboard-backspace-rounded" class="text-2xl" />
            <p class="text-2xl">На главную</p>
        </NuxtLink>
        <FormKit @submit="authUser" type="form" :actions="false" messages-class="hidden" form-class="flex flex-col gap-6 items-center justify-center">
            <p class="mainHeading">Вход</p>
            <div class="flex flex-col gap-4 md:w-2/3 lg:w-1/2">
                <FormKit v-model="userForm.phone" validation="required|matches:/^[7-8]{1}-[0-9]{3}-[0-9]{3}-[0-9]{2}-[0-9]{2}$/" :validation-messages="{ matches: 'Номер телефона должен быть в формате 7/8-xxx-xxx-xx-xx', }" messages-class="text-[#E9556D]" type="tel" placeholder="x-xxx-xxx-xx-xx" name="Номер телефона" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
                <FormKit v-model="userForm.password" validation="required|length:8" messages-class="text-[#E9556D]" type="password" placeholder="······" name="Пароль" outer-class="w-full" input-class="w-full px-4 py-1.5 rounded-xl bg-[#F4EFE6]"/>
            </div>
            <button :disabled="isAuthDisabled" :class="{ 'opacity-50 cursor-not-allowed': isAuthDisabled }" type="submit" class="cursor-pointer px-10 py-1.5 bg-[#E6F5EE] rounded-full text-center">Войти</button>
        </FormKit>
        <p class="text-xl ml-auto w-fit">Ещё нет аккаунта? <NuxtLink to="/reg" class="text-[#263AA7]">Зарегистрироваться</NuxtLink></p>
    </div>
</template>

<script setup>
/* создание формы пользователя */
const userForm = ref({
    phone: '',
    password: ''
})


/* создание сообщений и подключение хранилищ */
const { showMessage } = useMessagesStore()
const { login, loadProfileData } = useUserStore()


/* подключение БД и роутера */
const supabase = useSupabaseClient()
const router = useRouter()


/* вход */
const isAuthDisabled = ref(false)
const authUser = async() => {  
    isAuthDisabled.value = true
    const { data: user, error } = await supabase
    .from('users')
    .select("*")
    .eq('phone', userForm.value.phone)
    .single()

    if (!user) {
        userForm.value.phone = ""
        isAuthDisabled.value = false
        return showMessage("Неверный логин!", false)              
    }

    if (userForm.value.password !== user.password) {
        userForm.value.password = ""
        isAuthDisabled.value = false
        return showMessage('Неверно введен пароль!', false)            
    }

    showMessage('Успешный вход!', true)
    login(user.id, user.role)
    isAuthDisabled.value = false

    if(user.role === 'user') {
        router.push('/profile')
    }
    if(user.role === 'admin') {
        router.push('/admin')
    }
} 
</script>