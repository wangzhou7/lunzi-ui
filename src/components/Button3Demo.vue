<demo>
    支持 size
</demo>
<template>
    <div>
        <div>
            <Button size="big">Big</Button>
            <Button>Normal</Button>
            <Button size="small">Small</Button>
        </div>
        <div>
            <Button theme="text" size="big">Big</Button>
            <Button theme="text">Normal</Button>
            <Button theme="text" size="small">Small</Button>
        </div>
        <div>
            <Button theme="link" size="big">Big</Button>
            <Button theme="link">Normal</Button>
            <Button theme="link" size="small">Small</Button>
        </div>
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