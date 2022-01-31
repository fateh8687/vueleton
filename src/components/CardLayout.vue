<template>
    <div class="CardLayout">
        <Skeleton :width="100" :height="100" rounded />
        <div>
            <Skeleton :width="300" :height="100" />
            <Skeleton :width="300" :height="100" />
        </div>
    </div>
</template>

<script lang="ts" setup>
import Skeleton from './Skeleton.vue';

const props = defineProps({
    color: {
        type: String,
        default: 'gray'
    }
})

</script>

<style scoped lang="scss">
.CardLayout {
    display: flex;
    border: 1px solid lightgray;
    width: fit-content;
    padding: 10px;

    ::v-deep(.skeleton) {
        margin: 5px;
    }
}
</style>