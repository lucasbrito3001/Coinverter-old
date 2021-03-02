<template>
    <footer>
        <div class="follow-me">
            <h4>Siga-me:</h4>
            <ul id="social-networks">
                <li id="instagram">Instagram</li>
                <li id="linkedin">LinkedIn</li>
                <li id="github">GitHub</li>
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