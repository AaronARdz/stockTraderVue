<template>
    <div>
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <router-link class="navbar-brand" to="/" tag="a">Stock Trader</router-link>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
                <router-link class="nav-link" activeClass="active" to="/portfolio" tag="li">
                <a class="nav-link">Portfolio</a>
                </router-link>
                <router-link class="nav-link" activeClass="active" to="/stocks" tag="li">
                <a class="nav-link">Stocks</a>
                </router-link>
            </ul>
            <ul class="nav navbar-nav navbar-right">    
                <li class="nav-item"><a class="nav-link" href="#">End Day</a></li>   
                <li class="nav-item dropdown">
                    <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                    Save & Load
                    </a>
                    <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                    <a class="dropdown-item" href="#">Save</a>
                    <a class="dropdown-item" href="#">Load</a>
                    </div>
                </li>
            </ul>
        </div>  
        </nav>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>

</style>