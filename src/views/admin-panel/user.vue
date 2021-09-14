<template>
    <div>
        <v-data-table
                dense
                :headers="headers"
                :items="userList"
                class="mt-1"
                hide-default-footer
        ></v-data-table>
        <Paginate store="user" collection="userList" method="uploadUsers"/>
    </div>
</template>

<script>
    import {mapGetters} from 'vuex'
    import Paginate from "../../components/Paginate";

    export default {
        name: 'user',
        components: {Paginate},
        comments: {},
        data() {
            return {
                headers: [
                    {
                        text: 'ID',
                        divider: true,
                        value: 'id',
                        class: 'green lighten-2'
                    },
                    {
                        text: 'Foydalanuvchi',
                        divider: true,
                        value: 'full_name',
                        class: 'green lighten-2'
                    },
                    {
                        text: 'Login',
                        divider: true,
                        value: 'username',
                        class: 'green lighten-2'
                    },
                    {
                        text: "Amallar",
                        divider: true,
                        value: "actions",
                        class: "green lighten-2",

                    },
                ]
            }
        },
        created() {
            this.getUsers()
        },
        computed: {
            ...mapGetters({
                userList: 'user/getUsers',
                getCurrentPage: 'user/getCurrentPage'
            })
        },
        methods: {
            async getUsers() {
                try {
                    await this.$store.dispatch('user/uploadUsers', {
                        url: "/users?page=",
                        method: "get",
                        pageNumber: this.getCurrentPage,
                        body: {},
                    });
                } catch (error) {
                    this.$toast.error(error)
                }
            },
        }
    }
</script>

<style>

</style>