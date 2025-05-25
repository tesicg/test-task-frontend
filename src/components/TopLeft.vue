<template>
    <div class="list" v-if="selectedItems.length > 0">
        <div class="box" v-for="item in selectedItems" :key="item.id">
            <div>{{ item.name }}</div>
        </div>
    </div>
    <div v-else class="empty-message">Select 1-6 items from the bottom left</div>
</template>

<script setup>
defineProps({
    selectedItems: {
        type: Array,
        default: () => [],
        required: true,
    },
})
</script>

<style lang="scss" scoped></style>
