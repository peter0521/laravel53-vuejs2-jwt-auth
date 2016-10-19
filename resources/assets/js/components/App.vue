<template>
    <div class="panel panel-default">
        <div class="panel-heading">
            <nav>
                <ul class="list-inline">
                    <li><router-link to="home">Home</router-link></li>
                    <li class="pull-right" v-if="!auth.user.authenticated">
                        <router-link to="register">Register</router-link>
                    </li>
                    <li class="pull-right" v-if="!auth.user.authenticated">
                        <router-link to="signin">Sign in</router-link>
                    </li>
                    <li class="pull-right" v-if="auth.user.authenticated">
                        <a href="#" v-on:click="signout">Sign out</a>
                    </li>
                    <li class="pull-right" v-if="auth.user.authenticated">
                        Hi, {{ auth.user.profile.name }}
                    </li>
                </ul>
            </nav>
        </div>
        <div class="panel-body">
            <router-view></router-view>
        </div>
    </div>
</template>

<script>
    import auth from '../auth.js'

    export default {
        data() {
            return {
                auth: auth
            }
        },
        methods: {
            signout() {
                auth.signout()
            }
        },
        ready() {
            auth.check()
        }
    }
</script>