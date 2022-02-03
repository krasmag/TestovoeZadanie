<template>
    <div>
        <div class="uk-alert-danger" uk-alert v-if="error">
            <a class="uk-alert-close" uk-close></a>
            <p>Проверьте правильность введенный полей</p>
        </div>
        <form style="margin-bottom: 20px;">
            <fieldset class="uk-fieldset">

                <legend class="uk-legend">Опубликовать пост</legend>

                <div class="uk-margin">
                    <input class="uk-input" v-model="form.name" type="text" placeholder="ФИО">
                </div>

                <div class="uk-margin">
                    <span >Активен пользователь ?</span>
                    <input type="checkbox" v-model="form.act">
                </div>

                <button class="uk-button uk-button-primary" @click.prevent="store">
                    <div uk-spinner v-if="loading"></div>
                    <span v-else>Опубликовать</span>
                </button>
            </fieldset>

        </form>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        components: {},
        data: () => ({
            form: {
                name: "",
                act: ""
            },
            loading: false,
            error: false
        }),
        methods: {
            store() {
                this.loading = true;
                axios.post('/api/main', this.form, {
                    headers: {
                        "Content-type": "application/json"
                    }
                })
                .then(res => {
                    if (res.data.status) {
                        this.$router.push('/post/' + res.data.post.id);
                    } else {
                        setTimeout(() => {
                            this.loading = false;
                        }, 300);
                        this.error = true;
                    }
                })
            }
        }
    }
</script>

<style scoped>

</style>
