<template>
    <div>
        Hook
    </div>
</template>

<script>
import { onBeforeMount, onMounted, onBeforeUnmount, onUnmounted } from 'vue'
export default {
    setup() {
        onBeforeMount(() => {
            console.log('Before');
        })
        onMounted(() => {
            console.log('Mounted');
            })
        onBeforeUnmount(() => {
            console.log('beforUnmount')
        })
        onUnmounted(() => {
            console.log('Unmounted')
        })
    },
    
}
</script>