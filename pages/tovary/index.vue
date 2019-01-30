<template>
  <section class="tovary">
    <Breadcrumbs />
    <div class="container">
        <div class="tovary__title"><h1 v-html="params.title"></h1></div>
        <SidebarSearchParams />
        <div class="tovary__main">
            <SortOf />
            <div class="tovary__cards">
                <Card v-for="(item, i) in cardArray" :params="item" :key="`card101-${i}`"/>
            </div>
            <ShowMore :isActive="cardInList < cardInListMax" @showMore="showMore"/>


        </div>
    </div>
  </section>
</template>

<script>

export default {
    data() {
        return {
            cardInList: 4,
            cardInListMax: 12,
            actualList: 0,
            cardArray: [],
            params: {
                title: "Аксессуары и комплектующие для аудиотехники в Беларуси",
                cards: [
                {
                    imgSrc: "/img/photo/TG100.png",
                    description: "Крепление для акустики Beyerdynamic Rackmount Kit TG100",
                    price: 125.40,
                    instock: true,
                    phonePrefix: "+375 (17) 3",
                    phoneNamber: "33 33 33",
                    company: "Про 100",
                    companyLink: "www.pro100.by",
                    city: "г. Минск"
                },
                {
                    imgSrc: "/img/photo/GMB33S.png",
                    description: "Док-станция Beyerdynamic GMB 33 S",
                    price: 444.40,
                    instock: true,
                    phonePrefix: "+375 (29) 2",
                    phoneNamber: "33 33 33",
                    company: "Про 200",
                    companyLink: "www.pro200.by",
                    city: "г. Брест"
                },
                {
                    imgSrc: "/img/photo/ATN95E.png",
                    description: "Игла звукоснимателя Audio-Technica ATN95E",
                    price: 78.58,
                    instock: true,
                    phonePrefix: "+375 (29) 1",
                    phoneNamber: "33 33 33",
                    company: "Про 100",
                    companyLink: "www.pro100.by",
                    city: "г. Минск"
                },
                {
                    imgSrc: "/img/photo/WL001N.png",
                    description: "Указка-презентер лазерная 2х3 WL001 N",
                    price: 45.43,
                    instock: true,
                    phonePrefix: "+375 (29) 6",
                    phoneNamber: "33 33 33",
                    company: "Про 100",
                    companyLink: "www.pro100.by",
                    city: "г. Минск"
                },

                {
                    imgSrc: "/img/photo/WL002.png",
                    description: "Презентер 2х3 WL002",
                    price: 99.15,
                    instock: true,
                    phonePrefix: "+375 (29) 6",
                    phoneNamber: "33 33 33",
                    company: "Про 100",
                    companyLink: "www.pro100.by",
                    city: "г. Минск"
                },
                {
                    imgSrc: "/img/photo/AT-LP120BK.png",
                    description: "Проигрыватель виниловых дисков AUDIO-TECHNICA AT-LP120BK-USBS10",
                    price: 846.12,
                    instock: true,
                    phonePrefix: "+375 (29) 9",
                    phoneNamber: "33 33 33",
                    company: "Про 200",
                    companyLink: "www.pro200.by",
                    city: "г. Брест"
                },
                {
                    imgSrc: "/img/photo/ESI_U24_XL.png",
                    description: "Аудиоинтерфейс ESI U24 XL",
                    price: 245.70,
                    instock: true,
                    phonePrefix: "+375 (29) 2",
                    phoneNamber: "33 33 33",
                    company: "Про 100",
                    companyLink: "www.pro100.by",
                    city: "г. Минск"
                },
                {
                    imgSrc: "/img/photo/GMB_33_S.png",
                    description: "Док-станция Beyerdynamic GMB 33 S",
                    price: 444.40,
                    instock: true,
                    phonePrefix: "+375 (29) 6",
                    phoneNamber: "33 33 33",
                    company: "Про 100",
                    companyLink: "www.pro100.by",
                    city: "г. Минск"
                },

                {
                    imgSrc: "/img/photo/AT33PT_GII.png",
                    description: "Головка звукоснимателя AUDIO-TECHNICA AT33PT GII",
                    price: 958.78,
                    instock: false,
                    phonePrefix: "+375 (29) 9",
                    phoneNamber: "33 33 33",
                    company: "Про 100",
                    companyLink: "www.pro100.by",
                    city: "г. Минск"
                },
                {
                    imgSrc: "/img/photo/AT311EP.png",
                    description: "Картридж ММ-типа AUDIO-TECHNICA AT311EP",
                    price: 101.46,
                    instock: false,
                    phonePrefix: "+375 (29) 9",
                    phoneNamber: "33 33 33",
                    company: "Про 200",
                    companyLink: "www.pro200.by",
                    city: "г. Брест"
                },
                {
                    imgSrc: "/img/photo/ATN3472SE.png",
                    description: "Сменная игла AUDIO-TECHNICA ATN3472SE",
                    price: 74.14,
                    instock: false,
                    phonePrefix: "+375 (29) 2",
                    phoneNamber: "33 33 33",
                    company: "Про 100",
                    companyLink: "www.pro100.by",
                    city: "г. Минск"
                },
                {
                    imgSrc: "/img/photo/ATN3472P.png",
                    description: "Сменная игла AUDIO-TECHNICA ATN3472P",
                    price: 60.48,
                    instock: false,
                    phonePrefix: "+375 (29) 6",
                    phoneNamber: "33 33 33",
                    company: "Про 100",
                    companyLink: "www.pro100.by",
                    city: "г. Минск"
                }
            ]
            },

        }
    },

    mounted() {
        this.getCardArray();
    },

    methods: {
        getCardArray() {
            this.cardArray = [];
            this.params.cards.forEach((item, i) => {
                if ( i >= this.actualList * this.cardInList && i < (this.actualList + 1) * this.cardInList ) {
                    this.cardArray.push(item);
                }
            });
        },

        showMore() {
            this.cardInList += 4;
            this.getCardArray();
        }
    }
}
</script>

<style lang="scss">
    .tovary {
        min-height: calc(100vh - 120px);
        padding: 0 0 100px;
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

        &__main {
            display: inline-block;
            vertical-align: top;
            width: calc(100% - 340px);
        }

        &__cards {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            flex-wrap: wrap;
            padding: 40px 0 0;
            // margin: 0 -20px 0 0;
        }
    }
</style>

