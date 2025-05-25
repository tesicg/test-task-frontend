<template>
    <div class="list" v-if="selectedRightItem">
        <div class="box">
            <div>{{ selectedRightItem.name }}</div>
        </div>
    </div>
    <div v-else class="empty-message">Select 1 item from the bottom right</div>
</template>

<script setup>
defineProps({
    selectedRightItem: {
        type: Object,
        default: null,
        required: false,
    },
})
</script>

<style lang="scss" scoped></style>
