<template>
    <section class="bg-light-blue mb-3">
        <div class="p-3">
            <BaseTypography size="lg" weight="bold" class="mt-3 mb-4">
                {{ props.year }}년 {{ props.month }}월
            </BaseTypography>
            <BaseTypography size="lg" weight="bold"
                >총 수입:
                <span class="text-red">{{ props.income.toLocaleString() }}</span>
                원
            </BaseTypography>
            <BaseTypography size="lg" weight="bold" class="mb-3"
                >총 지출:
                <span class="text-blue">{{ props.spending.toLocaleString() }}</span>
                원
            </BaseTypography>
            <div class="row">
                <div class="col-6 col-sm-9"></div>
                <div class="col-6 col-sm-3">
                    <select class="form-select" v-model="selectedOption">
                        <option value="total">전체</option>
                        <option value="spending">지출</option>
                        <option value="income">수입</option>
                    </select>
                </div>
            </div>
        </div>
    </section>
</template>
<script setup>
import BaseTypography from '@/components/common/Typography/BaseTypography.vue'
import { computed, defineProps, defineEmits } from 'vue'
const props = defineProps({
    year: {
        type: Number,
    },
    month: {
        type: Number,
    },
    income: {
        type: Number,
    },
    spending: {
        type: Number,
    },
    selectedOption: {
        type: String,
        default: 'total',
    },
})
const emit = defineEmits(['update:selectedOption'])

const selectedOption = computed({
    get: () => props.selectedOption,
    set: (val) => emit('update:selectedOption', val),
})
</script>
