<template>
    <div class="show-more" :class="{ 'h-hide' : !isActive }">
        <div class="show-more__button" title="Добавить еще" @click.prevent="showMore()"></div>
    </div>
</template>

<script>
export default {
    props: {
        isActive: Boolean
    },
    methods: {
        showMore() {
            this.$emit('showMore', true);
        }
    }
}
</script>


<style lang="scss">
    .show-more {
        padding: 20px 0;

        &__button {
            height: 60px;
            background: #fff url(/img/icons/add.png) center center no-repeat;
            background-size: auto;
            border: 1px solid #ccc;
            cursor: pointer;
        }
    }
</style>
