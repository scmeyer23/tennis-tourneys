<template>
  <div class="home">
    <img alt="logo" src="../assets/logo.jpg">
    <h1>Welcome to the 2017 ATP Tour Homepage</h1>
    <div class="intro">
        <div class="sections">
            <h2>This website gives you access to every single ATP tournament played in 2017! If you go to the "Tournaments" tab you can scroll through all 67 of them and see the men's singles and doubles winners.</h2>
            <h2>At the "Favorites" tab you can see only those tournaments that you have selected on the "Tournaments" tab. To favorite a tournament, simply click the star in the top right corner. The four majors (Wimbledon, Roland Garros, The US Open, and The Australian Open) begin favorited.</h2>
        </div>
    </div>
  </div>
    
</template>

<style>
    .home img {
        margin-left: 40%;
        margin-right: 40%;
        width: 20%;
        height: 20%;
    }

    .home {
        background-color: white;
    }

    h1 {
        text-align: center;
    }

    .intro {
        grid-template: auto auto / 1fr 1fr;
        column-gap: 10px;
    }

    .sections {
        display: grid;
        grid-template: auto auto/ 1fr 1fr;
        width: 85%;
        margin: 0 auto;
        outline: solid;
        outline-color: #e29d0f;
        padding: 0 20px;
    }

    .sections h2 {
        text-decoration: none;
        text-align: left;
        font-size: x-large;
        padding: 0 10px;
    }

    @media(max-width: 900px) {
        .sections {
            grid-template: auto / 1fr;
        }
    }
</style>
