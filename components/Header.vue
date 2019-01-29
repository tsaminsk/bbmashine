<template>
    <div class="header">
        <div class="container">
            <ul>
                <li>
                    <nuxt-link to="/">Home</nuxt-link>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {

}
</script>


<style lang="scss">
    .header {
        height: 80px;

        .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 100%;
            height: 100%;
            background-color: gray;
            color: #fff;
        }

        &__nav {
            display: flex;
            justify-content: flex-end;
        }

        &__item {
            padding: 0 40px;
            font-size: 20px;
            text-transform: uppercase;

            a {
                // font-family: $Koedu;
                // font-weight: 500;
                text-decoration: none;
                color: #fff;
            }
        }
    }

</style>

