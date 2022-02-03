<template>
    <form method="delete" action="http://krastelev1/api/main/4">
    <div class="uk-card uk-card-default uk-width-1-2@m">
        <div class="uk-card-header">
            <div class="uk-grid-small uk-flex-middle" uk-grid>
                <div class="uk-width-expand">
                    <h3 class="uk-card-title uk-margin-remove-bottom">{{ title }}</h3>
                    <p class="uk-text-meta uk-margin-remove-top">
                        <time datetime="2016-04-01T19:00">{{ date }}</time>
                    </p>
                </div>
            </div>
        </div>
        <div class="uk-card-body">
            <p>Сотрудник онлайн: {{ body }}</p>
        </div>
        <!-- <div class="uk-card-footer">
            <input type="hidden" name="id" v-bind:value="id">
            <input type="submit" value="Удалить">
        </div> -->
    </div>
    </form>
</template>

<script>
    export default {
        props: {
            title: {
                type: String,
                default: "NULL"
            },
            body: {
                type: Boolean,
                default: "НЕТ"
            },
            date: {
                type: String,
                default: "NULL"
            },
            id:   {
                type: Number,
                default: "NULL"
            }
        }
    }
</script>

<style scoped>

</style>
