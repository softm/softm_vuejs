<template>
    <div>
        User List
        <div v-for="user in users" :key="user.id">
            {{ user.name }}
        </div>
    </div>
</template>

<script>
    import {mapState,mapActions} from 'vuex';

    export default {
        created() {
            this.getUsers();
        },
        computed: {
            ...mapState('user',['users']
/*
                {
                    people:state => state.users
                }
*/
/*                                 
                {
                    people:state => state.user.users
                }
*/
/*
                {
                    // 'todos',                    
                    people:'users'
                } 
*/
/*
                [
                    // 'todos',                    
                    'users'
                ],
*/
            )
            // users() {
            //     return this.$store.state.users;
            // }
        },
        methods: {
            ...mapActions('user',['getUsers'])
            // ...mapActions(['getUsers'])
            // getUsers() {
            //     this.$store.dispatch('getUsers');
            // }
        }
    }
</script>