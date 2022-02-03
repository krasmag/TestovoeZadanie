<template>
    <nav class="uk-navbar-container" uk-navbar>
        <div class="uk-navbar-center">

            <ul class="uk-navbar-nav">
<!--                class="uk-active"-->
                <li v-for="link in links" v-bind:key="link" v-bind:link="link">
                    <router-link :to="link.href">{{ link.title }}</router-link>
                </li>
            </ul>

        </div>
    </nav>
</template>

<script>
    export default {
        data() {
            return {
                links: [
                    {
                        title: "Главная",
                        href: "/"
                    },
                    {
                        title: "Персонал",
                        href: "/personal"
                    },
                    {
                        title: "Добавить сотрудника",
                        href: "/add"
                    }
                ]
            }
        }
    }
</script>

<style scoped>

</style>
