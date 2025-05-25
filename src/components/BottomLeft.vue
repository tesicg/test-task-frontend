<template>
    <div class="list">
        <div
            class="box"
            v-for="item in data"
            :key="item.id"
            :class="{ selected: isSelected(item) }"
            @click="toggleSelection(item)"
        >
            <div>{{ item.name }}</div>
        </div>
    </div>
    <div class="selection-info">Selected: {{ selectedItems.length }}/6</div>
</template>

<script setup>
import { ref } from 'vue'

defineProps({
    data: {
        type: Array,
        required: true,
    },
})

const emit = defineEmits(['sendLeftData'])

// Track selected items for left side (multiple selection)
const selectedItems = ref([])
const MAX_SELECTION = 6

// Toggle item selection for left side
function toggleSelection(item) {
    const index = selectedItems.value.findIndex((i) => i.id === item.id)

    if (index > -1) {
        // If already selected, remove it
        selectedItems.value.splice(index, 1)
    } else if (selectedItems.value.length < MAX_SELECTION) {
        // If not selected and under max limit, add it
        selectedItems.value.push(item)
    } else {
        // Optional: Show a message that max selection is reached
        alert('Maximum selection of 6 items reached')
    }
    emit('sendLeftData', selectedItems)
}

// Check if an item is selected in left side
function isSelected(item) {
    return selectedItems.value.some((i) => i.id === item.id)
}
</script>

<style lang="scss" scoped></style>
