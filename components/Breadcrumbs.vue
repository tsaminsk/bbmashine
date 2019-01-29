<template>
    <div class="breadcrumbs">
        <div class="container">
            <div class="breadcrumbs__item breadcrumbs__item-home">
                <nuxt-link to="/">
                    <img src="/img/icons/home.png" alt="">
                </nuxt-link>
            </div>
            <div class="breadcrumbs__item"
                v-for="(item, i) in params.links"
                :key="`abc-${i}`"
            >
                <nuxt-link :to="item.link"
                    v-html="item.name"
                    :class="{ 'is-active' : i === params.links.length - 1}"
                />
                <span v-if="i === params.links.length - 1">({{params.total}})</span>
            </div>

        </div>

    </div>
</template>
<script>
export default {
    data() {
        return {
            params: {
                links: [
                    {name: "Товары", link: "/"},
                    {name: "Аудио, видео, фото", link: "/"},
                    {name: "Аудиотехника и hi-fi аппаратура", link: "/"},
                    {name: "Аксессуары и комплектующие для аудиотехники", link: "/"}
                ],
                total: 64
            }
        }
    }
}


</script>


<style lang="scss">
    .breadcrumbs {
        height: 90px;

        .container {
            display: flex;
            justify-content: flex-start;
            align-items: center;
            height: 100%;
            padding: 20px 6.66%;
        }

        &__item {
            padding: 0 0 0 20px;

            &::before {
                content: '/';
                padding: 0 20px 0 0;
            }

            a {
                color: blue;
                text-decoration: none;

                &.is-active {
                    color: grey;
                    pointer-events: none;
                }
            }

            span {
                color: grey;
            }
        }

        &__item-home {
            width: 60px;
            height: 60px;
            padding: 0;
            margin: 5px -20px -5px -10px;

            &::before {
                display: none;
            }
        }
    }
</style>
