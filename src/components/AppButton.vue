<template>
    <div>
        {{ variant }}
        <button @click="sendData">
            <slot></slot>
            <slot name="icon"></slot>
        </button>
    </div>
</template>

<script>
export default {
    props: {
        variant: {
            type: String,
            default: 'success'
        }
    },
    setup(props, {slots, emit}) {
        console.log(slots);

        const sendData = () => {
            emit('update', props.variant)
        }

        return {
            sendData
        }
    }
}
</script>