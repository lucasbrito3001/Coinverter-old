<template>
    <header>
        <nav class="navbar navbar-expand-md navbar-light bg-light">
            <a class="navbar-brand" href="#">Logo</a>
            <button type="button" class="navbar-toggler" data-toggle="collapse" data-target="#navbarCollapsible">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div id="navbarCollapsible" class="collapse navbar-collapse">
                <ul class="navbar-nav">
                    <li class="nav-item"><a class="nav-link" href="#">Conversor de Moedas</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Notícias Relevantes</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Tabela de Cotações</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Bitcoin</a></li>
                </ul>
                
                <ul class="navbar-nav ml-auto">
                    <li class="nav-item">
                        <a href="#" class="nav-link">Dark Mode</a>
                    </li>
                </ul>
            </div>
        </nav>
    </header>    
</template>

<script>
export default {
    
}
</script>

<style scoped>

.navbar-nav .nav-item{
    margin: 0 10px;
}

.navbar-toggler:focus{
    outline: .5px solid rgb(170, 170, 170);
}

.navbar-brand {
    font-size: 1rem;
}
</style>