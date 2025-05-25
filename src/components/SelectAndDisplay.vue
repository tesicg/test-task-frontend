<template>
    <div class="container">
        <div id="topLeft" class="top-left">
            <top-left :selectedItems="selectedItems" />
        </div>
        <div id="topRight" class="top-right">
            <top-right :selectedRightItem="selectedRightItem" />
        </div>
        <div id="bottomLeft" class="bottom-left">
            <bottom-left :data="leftData" @send-left-data="onSendLeftData" />
        </div>
        <div id="bottomRight" class="bottom-right">
            <bottom-right :data="rightData" @send-right-data="onSendRightData" />
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import TopLeft from './TopLeft.vue'
import TopRight from './TopRight.vue'
import BottomLeft from './BottomLeft.vue'
import BottomRight from './BottomRight.vue'

const selectedItems = ref([])
const selectedRightItem = ref(null)

const leftData = ref([
    { id: 1, name: 'Shoes 1' },
    { id: 2, name: 'Shoes 2' },
    { id: 3, name: 'Shoes 3' },
    { id: 4, name: 'Shoes 4' },
    { id: 5, name: 'T-shirt 1' },
    { id: 6, name: 'T-shirt 2' },
    { id: 7, name: 'T-shirt 3' },
    { id: 8, name: 'T-shirt 4' },
])

const rightData = ref([
    { id: 11, name: 'Jacket 1' },
    { id: 12, name: 'Jacket 2' },
    { id: 13, name: 'Jacket 3' },
    { id: 14, name: 'Jacket 4' },
    { id: 15, name: 'Hoodie 1' },
    { id: 16, name: 'Hoodie 2' },
    { id: 17, name: 'Hoodie 3' },
    { id: 18, name: 'Hoodie 4' },
])

function onSendLeftData(data) {
    selectedItems.value = [...data.value]
}

function onSendRightData(data) {
    selectedRightItem.value = data.value
}
</script>

<style scoped></style>
