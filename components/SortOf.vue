<template>
    <div class="sort-of">
        <div class="sort-of__title">Показывать сначала:</div>
        <div class="sort-of__item"
            v-for="(item, i) in params"
            :class="{ 'is-active' : i === activeNum}"
            :key="`sort-of-${i}`"
            v-html="item"
            @click="activeNum = i"
            ></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            activeNum: 0,
            params: [
                "По рейтингу",
                "Сначала подешевле",
                "Сначала подороже",
                "Со скидками"
            ]
        }
    }

}
</script>


<style lang="scss">
    .sort-of {
        padding: 15px 0 15px 20px;
        text-align: left;
        border: 1px solid #ccc;
        background-color: #fff;

        &__title,
        &__item {
            display: inline-block;
            padding: 5px 0 10px;
            margin: 0 30px 0 0;
        }

        &__item {
            border-bottom: 2px solid #ccc;
            cursor: pointer;

            &.is-active {
                border-bottom: 2px solid red;
            }
        }


    }
</style>
