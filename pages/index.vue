<template>
  <section class="home">
    <div class="container">
        <div>
            <h1 class="home__title">
                bbmashine test work
            </h1>
            <h2 class="home__subtitle">
                Nuxt.js project
            </h2>
            <div class="home__links">
                <nuxt-link to="/tovary">Test page</nuxt-link>
            </div>
        </div>
    </div>
  </section>
</template>

<script>

export default {

}
</script>

<style lang="scss">
    .home {
        min-height: calc(100vh - 120px);
        background-color: #f8f8f8;

        &__title {
            display: block;
            font-weight: 300;
            font-size: 100px;
            color: #35495e;
            letter-spacing: 1px;
            text-transform: uppercase;
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

