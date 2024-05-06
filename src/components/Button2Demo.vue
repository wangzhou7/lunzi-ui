<demo>
    支持 level
</demo>
<template>
    <div>
        <div>
            <Button level="main">Main button</Button>
            <Button>Normal button</Button>
            <Button level="danger">Danger button</Button>
        </div>
        <div>
            <Button theme="text" level="main">Main text button</Button>
            <Button theme="text">Normal Text button</Button>
            <Button theme="text" level="danger">Danger text button</Button>
        </div>
        <div>
            <Button theme="link" level="main">Main link button</Button>
            <Button theme="link">Normal link button</Button>
            <Button theme="link" level="danger">Danger link button</Button>
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