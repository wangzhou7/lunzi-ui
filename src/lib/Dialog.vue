<template>
    <template v-if="visible">
        <teleport to='body' />
        <div class="lunzi-dialog-overlay" @click="onClickoverly"></div>
        <div class="lunzi-dialog-wrapper">
            <div class="lunzi-dialog">
                <header>
                    <slot name="title" />
                    <span class="lunzi-dialog-close" @click="close"></span>
                </header>
                <main>
                    <slot name="content" />
                </main>
                <footer>
                    <Button level="main" @click="OK"> OK </Button>
                    <Button @click="Cancel"> Cancel </Button>
                </footer>
            </div>
        </div>
    </template>
</template>

<script lang="ts">
import Button from "./Button.vue";
export default {
    props: {
        title: {
            type: String,
            default: '提示'
        },
        visible:
        {
            type: Boolean,
            default: false
        },
        closeOnClickoverly: {
            type: Boolean,
            default: false
        },
        ok: {
            type: Function
        },
        cancel: {
            type: Function
        }
    },

    components:
    {
        Button
    },

    setup(props, context) {
        const close = () => {
            context.emit('update:visible', false)
        }
        const OnClickoverly = () => {
            if (props.closeOnClickoverly) {
                close()
            }
        }
        const OK = () => {
            if (props.ok?.() !== false) {
                close()
            }
        }
        const Cancel = () => {
            props.cancel?.()
            close()
        }
        return { close, OnClickoverly, OK, Cancel }
    }
}
</script>

<style lang="scss">
$radius: 4px;
$border-color: #d9d9d9;

.lunzi-dialog {
    background: white;
    border-radius: $radius;
    box-shadow: 0 0 3px fade_out(black, 0.5);
    min-width: 30em;
    max-width: 90%;
    min-height: 15em;
    max-height: 90%;

    &-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: fade_out(black, 0.5);
        z-index: 10;
    }

    &-wrapper {
        position: fixed;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        z-index: 11;
    }

    >header {
        padding: 12px 16px;
        border-bottom: 1px solid $border-color;
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-size: 20px;
    }

    >main {
        padding: 12px 16px;
    }

    >footer {
        border-top: 1px solid $border-color;
        padding: 12px 16px;
        text-align: right;
    }

    &-close {
        position: relative;
        display: inline-block;
        width: 16px;
        height: 16px;
        cursor: pointer;

        &::before,
        &::after {
            content: '';
            position: absolute;
            height: 1px;
            background: black;
            width: 100%;
            top: 50%;
            left: 50%;
        }

        &::before {
            transform: translate(-50%, -50%) rotate(-45deg);
        }

        &::after {
            transform: translate(-50%, -50%) rotate(45deg);
        }
    }
}
</style>