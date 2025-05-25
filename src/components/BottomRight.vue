<template>
    <div class="list">
        <div
            class="box"
            v-for="item in data"
            :key="item.id"
            :class="{ 'selected-right': isSelectedRight(item) }"
            @click="selectRightItem(item)"
        >
            <div>{{ item.name }}</div>
        </div>
    </div>
    <div class="selection-info">Selected: {{ selectedRightItem ? 1 : 0 }}/1</div>
</template>

<script setup>
import { ref } from 'vue'

defineProps({
    data: {
        type: Array,
        required: true,
    },
})

const emit = defineEmits(['sendRightData'])

// Track selected item for right side (single selection)
const selectedRightItem = ref(null)

// Select a single item from right side
function selectRightItem(item) {
    // If the same item is clicked again, deselect it
    if (selectedRightItem.value && selectedRightItem.value.id === item.id) {
        selectedRightItem.value = null
    } else {
        // Otherwise, select the new item
        selectedRightItem.value = item
    }
    emit('sendRightData', selectedRightItem)
}

// Check if an item is selected in right side
function isSelectedRight(item) {
    return selectedRightItem.value && selectedRightItem.value.id === item.id
}
</script>

<style lang="scss" scoped></style>
