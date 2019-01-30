<template>
  <section class="tovary">
    <Breadcrumbs />
    <div class="container">
        <div class="tovary__title"><h1 v-html="params.title"></h1></div>
        <SidebarSearchParams />
        <div class="tovary__main">
            <SortOf />
            <div class="tovary__cards">
                <Card v-for="(item, i) in cards" :params="item" :key="`card101-${i}`"/>


            </div>



        </div>
    </div>
  </section>
</template>

<script>

export default {
    data() {
        return {
            params: {
                title: "Аксессуары и комплектующие для аудиотехники в Беларуси",
            },
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
                    imgSrc: "/img/photo/TG100.png",
                    description: "Крепление для акустики Beyerdynamic Rackmount Kit TG100",
                    price: 125.40,
                    instock: true,
                    phonePrefix: "+375 (17) 3",
                    phoneNamber: "33 33 33",
                    company: "Про 100",
                    companyLink: "www.pro100.by",
                    city: "г. Минск"
                }
            ]
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

