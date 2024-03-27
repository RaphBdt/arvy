<template>
    <RadioGroup v-model="selected">
        <RegistrationStepTitle title="Type de compte" description="Choisissez un type de compte" />
        <RadioGroupLabel class="sr-only">Privacy setting</RadioGroupLabel>
        <div class="-space-y-px rounded-md bg-white">
            <div class="mb-5">
                <RadioGroupOption as="template" v-for="(setting, settingIdx) in settings" :key="setting.name"
                    :value="setting" v-slot="{ checked, active }">
                    <div
                        :class="[settingIdx === 0 ? 'rounded-tl-md rounded-tr-md' : '', settingIdx === settings.length - 1 ? 'rounded-bl-md rounded-br-md' : '', checked ? 'z-10 border-violet-200 bg-violet-50' : 'border-gray-200', 'relative flex cursor-pointer border p-4 focus:outline-none']">
                        <span
                            :class="[checked ? 'bg-violet-600 border-transparent' : 'bg-white border-gray-300', active ? 'ring-2 ring-offset-2 ring-violet-600' : '', 'mt-0.5 h-4 w-4 shrink-0 cursor-pointer rounded-full border flex items-center justify-center']"
                            aria-hidden="true">
                            <span class="rounded-full bg-white w-1.5 h-1.5" />
                        </span>
                        <span class="ml-3 flex flex-col">
                            <RadioGroupLabel as="span"
                                :class="[checked ? 'text-violet-900' : 'text-gray-900', 'block text-sm font-medium']">{{
        setting.name }}</RadioGroupLabel>
                            <RadioGroupDescription as="span"
                                :class="[checked ? 'text-violet-700' : 'text-gray-500', 'block text-sm']">{{
        setting.description }}</RadioGroupDescription>
                        </span>
                    </div>
                </RadioGroupOption>
            </div>
            <AppButton class="w-full" name="Continuer" color="violet" @click="clickBtnNext()" />
        </div>
    </RadioGroup>
</template>

<script setup>
import { ref } from 'vue'
import { RadioGroup, RadioGroupDescription, RadioGroupLabel, RadioGroupOption } from '@headlessui/vue'

const emit = defineEmits(['changeStepEvent', 'updateRegistrationEvent'])

const settings = [
    { name: 'Je suis CrossFiteur 💪', description: 'Je suis pratiquant de CrossFit dans une box affiliée ou du cross training' },
    { name: 'Je suis gérant ou coach 💼', description: 'Je suis gérant ou coach d\'une box et je souhaite découvrir Arvy' },
]

const selected = ref(settings[0])

function clickBtnNext() {
    emit('updateRegistrationEvent', { type: selected.value.name })
    emit('changeStepEvent')
}
</script>

<style scoped></style>