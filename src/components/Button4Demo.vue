<demo>
    支持 disabled
</demo>
<template>
    <div>
        <Button disabled> Disable button </Button>
        <Button theme="text" disabled>Disable text button</Button>
        <Button theme="link" disabled>Disable link button</Button>
    </div>
</template>

<script lang="ts">
import Button from "../lib/Button.vue";
export default {
    components: {
        Button
    }
}
</script>