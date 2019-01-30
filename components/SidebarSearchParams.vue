<template>
    <div class="sidebarsearchparams">
        <div class="sidebarsearchparams__item sidebarsearchparams__item-region">
            <p>Регион</p>
            <span v-for="(item, i) in params.regions"
                :key="`region${i}`"
                v-html="item"
                @click="changeRegion(item)"
                ></span>
        </div>
        <div class="sidebarsearchparams__item sidebarsearchparams__item-price">
            <div class="sidebarsearchparams__item-nav">
                <p>Цена, руб</p>
                <span class="sidebarsearchparams__item-open" :class="{ 'is-open' : changePrice }" @click="changePrice = !changePrice"></span>
            </div>
            <div class="sidebarsearchparams__item-main" v-if="changePrice">
                <form action="#">
                    <div>
                        <input type="text" v-model.trim="minPrice">
                        <span>-</span>
                        <input type="text" v-model.trim="maxPrice">
                        <input type="submit" value="OK">
                    </div>
                    <div class="sidebarsearchparams__item-main--runner" ref="runner">
                        <div class="sidebarsearchparams__item-main--runner_start" :style="'left: ' + runnerStartPos + 'px;'"></div>
                        <div class="sidebarsearchparams__item-main--runner_actual" :style="'left: ' + (runnerStartPos + 16) + 'px; right: ' + (runnerEndPos + 16) + 'px;'"></div>
                        <div class="sidebarsearchparams__item-main--runner_end" :style="'right: ' + runnerEndPos + 'px;'"></div>
                    </div>
                    <div>
                        <label>
                            <input type="checkbox" v-model="provenCompanies">
                            Проверенные компании
                        </label>
                        <span class="is-icon">?</span>
                    </div>
                </form>




            </div>

        </div>
        <div class="sidebarsearchparams__item">
            <div class="sidebarsearchparams__item-nav">
                <p>Производитель</p>
                <span class="sidebarsearchparams__item-open" :class="{ 'is-open' : changeFabricator }" @click="changeFabricator = !changeFabricator"></span>
            </div>
            <div class="sidebarsearchparams__item-main" v-if="changeFabricator">
                <form action="#">
                    <p v-for="(item, i) in params.allFabricators" :key="`fabricators-${i}`">
                        <label>
                            <input type="checkbox" :value="item" v-model="fabricators">
                            {{ item }}
                        </label>

                    </p>
                </form>
            </div>
        </div>
        <div class="sidebarsearchparams__item">
            <div class="sidebarsearchparams__item-nav">
                <p>Страна производства</p>
                <span class="sidebarsearchparams__item-open" :class="{ 'is-open' : countryOfOrigin }" @click="countryOfOrigin = !countryOfOrigin"></span>
            </div>
            <div class="sidebarsearchparams__item-main" v-if="countryOfOrigin">
                <form action="#">
                    <p v-for="(item, i) in params.allCuntry" :key="`cuntryes-${i}`">
                        <label>
                            <input type="checkbox" :value="item" v-model="cuntryes">
                            {{ item }}
                        </label>

                    </p>
                </form>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    data() {
        return {
            countryOfOrigin: false,
            cuntryes: [],
            changeFabricator: true,
            fabricators: [],
            provenCompanies: false,
            changePrice: true,
            minPrice: 0,
            maxPrice: 2999,
            runnerLength: null,
            runnerStartPos: 0,
            runnerEndPos: 0,
            params: {
                allFabricators: ["Beyerdynamic", "Audio-Technica", "2x3", "Athletic", "Sony"],
                allCuntry: ["Japan", "USA", "China", "Germany", "Russia"],
                regions: ["Беларусь"],
                items: [
                    {name: "", type: "", list: ["", ""]}
                ]
            }
        }
    },

    mounted() {
        this.runnerLength = this.$refs.runner.clientWidth;
        this.setPositions();
        console.log(this.runnerLength);
    },

    methods: {
        setPositions() {
            if ( this.minPrice < 0 ) {
                this.minPrice = 0;
            }
            else if ( this.minPrice >= this.maxPrice ) {
                this.minPrice = this.maxPrice - 1;
            }

            this.runnerStartPos = this.runnerLength * this.minPrice / 2999;

            if ( this.maxPrice > 2999 ) {
                this.runnerEndPos = this.runnerLength;
                this.maxPrice = 2999;
            }
            else if ( this.maxPrice > this.minPrice ) {
                this.runnerEndPos = this.runnerLength - this.runnerLength * this.maxPrice / 2999;
            }
            else {
                this.maxPrice = this.minPrice + 1;
                this.runnerEndPos = this.runnerLength - this.runnerLength * this.maxPrice / 2999;
            }
        },

        changeRegion(data) {
            console.log(data);
        }
    },

    watch: {
        minPrice() {
            this.setPositions();
        },
        maxPrice() {
            this.setPositions();
        }
    }

}
</script>


<style lang="scss">
    .sidebarsearchparams {
        display: inline-block;
        width: 300px;
        padding: 0 0 40px;
        border: 1px solid #ccc;
        background-color: #fff;
        margin: 0 2% 0 0;

        &__item {
            padding: 30px 15px;
            border-bottom: 1px solid #eee;

            p {
                display: inline-block;
                padding: 0 20px 0 0;
                font-weight: 700;
            }
        }

        &__item-region {
            span {
                font-weight: 400;
                text-decoration: underline;
                cursor: pointer;
            }
        }

        &__item-nav {
            position: relative;
            margin: 0 0 30px;
        }

        &__item-open {
            position: absolute;
            top: 50%;
            right: 10px;
            display: block;
            width: 10px;
            height: 10px;
            border-left: 2px solid #202020;
            border-bottom: 2px solid #202020;
            transform: rotate(-45deg);
            cursor: pointer;

            &.is-open {
                transform: rotate(135deg);
            }
        }

        &__item-main {

            form > div {
                margin: 0 0 30px;

                &:last-child {
                    margin: 0;
                }
            }

            form > p {
                display: block;
                font-size: 14px;
                font-weight: 400;
            }

            input {
                max-width: 100px;
                height: 40px;
                font-size: 20px;
                padding: 10px;
            }

            input[type="submit"] {
                float: right;
                width: 40px;
                padding: 0;
            }

            &--runner {
                position: relative;
                height: 1px;
                background-color: #ccc;
                margin: 0 0 20px;
            }

            &--runner_start,
            &--runner_end {
                position: absolute;
                top: -8px;
                width: 16px;
                height: 16px;
                border: 1px solid #ccc;
                background-color: #fff;
            }

            &--runner_actual {
                position: absolute;
                top: 0;
                height: 1px;
                background-color: red;
            }

            span.is-icon {
                display: block;
                float: right;
                width: 25px;
                height: 25px;
                padding: 2px 0 0;
                color: #fff;
                text-align: center;
                border-radius: 50%;
                background-color: #202020;
                margin: 5px 0 -5px;
                cursor: pointer;
            }
        }


    }
</style>
