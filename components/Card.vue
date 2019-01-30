<template>
    <div class="card" :class="{ 'is-active' : isActive }" @click.prevent="isActive = !isActive">
        <div class="card__img" :style="'background-image: url(' + params.imgSrc + ')'">

        </div>
        <div class="card__description" v-html="params.description">

        </div>
        <div class="card__price">
            <span v-html="params.price.toFixed(2)"></span>
            руб.
        </div>
        <div class="card__instock">
            <div class="card__instock-true" v-if="params.instock"><span>&#10004;</span>В наличии</div>
            <div class="card__instock-false" v-else>Нет в наличии</div>


        </div>
        <div class="card__phone">
            <div class="card__phone-button">
                <div class="card__phone-prefix" v-html="params.phonePrefix"></div>
                <div class="card__phone-hidenumber" v-if="!showPhone" @click="showPhone = !showPhone">показать</div>
                <div class="card__phone-number" v-else v-html="params.phoneNamber" @click="showPhone = !showPhone"></div>
            </div>

        </div>
        <div class="card__seller-info" v-if="isActive">
            <div class="card__seller-info--row">
                <div class="card__order card__phone-button">Заказать</div>
                <div class="card__favorite card__phone-button" title="Добавить в избранное"></div>
            </div>
            <div class="card__seller-info--row" v-if="params.company">
                <div class="card__seller-name" >
                    <nuxt-link :to="params.companyLink">Компания &laquo;<span v-html="params.company"></span>&raquo;</nuxt-link>
                </div>
                <div class="card__seller-company_info" title="Информация о компании и скидках">?%</div>
            </div>
            <div class="card__seller-info--row" v-if="params.city">
                <div class="card__seller-city" v-html="params.city"></div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    props: {
        params: Object
    },

    data() {
        return {
            showPhone: false,
            isActive: false,
        }
    }

}
</script>


<style lang="scss">
    .card {
        display: inline-block;
        width: calc(25% - 20px);
        min-height: 520px;
        border: 1px solid #ccc;
        background-color: #fff;

        margin: 0 0 40px;

        &__img {
            height: 300px;
            background: none center center no-repeat;
            background-size: auto 100%;
            margin: 0 0 10px;
        }

        &__description,
        &__price,
        &__phone {
            padding: 0 15px 7px;
            font-size: 18px;
            font-weight: 500;
        }

        &__description {
            height: 90px;
        }

        &__price span {
            padding: 0 5px 0 0;
            font-weight: 700;
        }

        &__instock {
            padding: 0 15px 10px;
            font-size: 14px;
            font-weight: 400;
        }

        &__instock-true {
            color: green;

            span {
                display: inline-block;
                vertical-align: middle;
                width: 20px;
                height: 20px;
                line-height: 1.3;
                text-align: center;
                border: 1px solid green;
                border-radius: 50%;
                margin: 0 10px 0 0;
            }

        }

        &__phone-button {
            padding: 10px 0;
            border: 1px solid #ccc;
        }

        &__phone {
            text-align: center;

            &-prefix,
            &-hidenumber,
            &-number {
                display: inline-block;
            }

            &-hidenumber {
                font-size: 16px;
                color: #00BFFF;
                border-bottom: 1px dashed #00BFFF;
                cursor: pointer;
            }

            &-number {
                cursor: pointer;
            }
        }

        &__seller-info {
            padding: 10px 15px 7px;
            font-size: 14px;
            font-weight: 300;
        }

        &__seller-info--row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 5px 0;

            div {
                display: inline-block;
                vertical-align: top;
            }
        }

        &__order {
            width: calc(100% - 60px);
            font-size: 16px;
            font-weight: 500;
            color: #fff;
            text-align: center;
            background-color: red;
            transition: color 0.25s linear, background-color 0.25s linear;
            cursor: pointer;

            &:hover {
                color: red;
                background-color: #fff;
            }
        }

        &__favorite {
            width: 50px;
            height: 46px;
            background-image: url(/img/icons/heart.png);
            background-size: cover auto;
            cursor: pointer;
        }

        &__seller-name a {
            color: #202020;
            text-decoration: none;

            &:hover {
                color: blue;
            }
        }

        &__seller-company_info {
            width: 30px;
            height: 30px;
            padding: 4px 0 0;
            text-align: center;
            border: 1px solid #ccc;
            border-radius: 50%;
            cursor: pointer;

            &:hover {
                padding: 3px 0 0;
                border-width: 2px;
                font-weight: 700;
            }
        }

        &__seller-city {
            color: #888;
        }

        &.is-active {
            box-shadow: 5px 0 7px -4px #9E9E9E, -5px 0 7px -4px #9E9E9E;
        }

    }
</style>
