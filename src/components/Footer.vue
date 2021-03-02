<template>
    <footer>
        <div class="follow-me">
            <h4>Siga-me:</h4>
            <ul id="social-networks">
                <li id="instagram"><a href="https://www.instagram.com/lucasdebrito12/" target="blank">Instagram</a></li>
                <li id="linkedin"><a href="https://www.linkedin.com/in/webdevbrito" target="blank">LinkedIn</a></li>
                <li id="github"><a href="https://github.com/lucasbrito3001" target="blank">GitHub</a></li>
            </ul>
        </div>
    </footer>    
</template>

<script>
export default {
    
}
</script>

<style scoped>
    footer{
        margin-top: 10vh;
        border-top: 5px solid var(--result);
        padding: 10px;
    }

    .follow-me{
        display: flex;
        justify-content: space-between;
    }

    .follow-me h4{
        width: 25%;
        text-align: center;
    }

    #social-networks{
        display: flex;
        justify-content: space-around;
        list-style: none;
        width: 75%;
    }
</style>