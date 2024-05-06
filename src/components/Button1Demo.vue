<demo>
    常规使用
</demo>
<template>
    <div>
        <Button @click="onClick">hello</Button>
        <Button theme="button">hello</Button>
        <Button theme="text">hello</Button>
        <Button theme="link">hello</Button>
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