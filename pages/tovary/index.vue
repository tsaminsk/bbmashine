<template>
  <section class="tovary">
    <Breadcrumbs />
    <div class="container">
        <div class="tovary__title" v-html="params.title">
        </div>
        <SidebarSearchParams />
        <div>

        </div>
    </div>
  </section>
</template>

<script>

export default {
    data() {
        return {
            params: {
                title: "<h1>Аксессуары и комплектующие для аудиотехники в Беларуси</h1>",
            }
        }
    }

}
</script>

<style lang="scss">
    .tovary {
        min-height: calc(100vh - 120px);
        background-color: #f8f8f8;

        &__title {
            padding: 0 0 60px;
            h1 {
                font-weight: 600;
                font-size: 30px;
                color: #202020;
            }
        }

        &__subtitle {
            font-weight: 300;
            font-size: 42px;
            color: #526488;
            word-spacing: 5px;
            padding-bottom: 15px;
        }

        &__links {
            padding-top: 15px;
        }
    }
</style>

