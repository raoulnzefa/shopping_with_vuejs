<template>
  <v-app>
      <v-data-table
        dense
        :headers="headers"
        :items="users"
        class="mt-1"
        hide-default-footer
      ></v-data-table>
      <p>hdskjfhsdjk</p>
  </v-app>
</template>

<script>
export default {
    name: 'user',
    data(){
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
    }
}
</script>

<style>

</style>