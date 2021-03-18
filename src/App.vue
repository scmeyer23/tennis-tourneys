<template>
    <div id="app">
        <div class="header">
            <h1>ATP Tournaments</h1>
            <div id="nav">
                <router-link to="/">Home</router-link> |
                <router-link to="/Tourneys">Tournaments</router-link> |
                <router-link to ="/Favorites">Favorites</router-link>
            </div>
        </div>
        <div class="content">
            <router-view />
        </div>
        <footer>
            <hr />
            <a href="https://github.com/scmeyer23/tennis-tourneys" target="_blank">GitHub Repo</a>
        </footer>
    </div>
</template>

<style>
    body {
        margin: 0px;
    }

    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
    }

    .header {
        display: flex;
        justify-content: space-between;
        background: #0b7d72;
        padding: 10px 100px;
        color: white;
    }

    #nav {
        padding: 30px;
    }

        #nav a {
            font-weight: bold;
            color: #fff;
        }

            #nav a.router-link-exact-active {
                color: #e29d0f;
            }

    .content {
        padding: 0px 100px;
        background-color: lightgrey;
    }

    footer{
        margin: 20px;
    }

    footer a {
        color: #0b7d72;
    }
</style>
