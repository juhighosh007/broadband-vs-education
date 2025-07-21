<script>
    let { children } = $props();
</script>

<div class="article-text">
    <p>
        {@render children()}
    </p>
</div>

<style>
    .article-text {
        margin: 50vh auto;
        width: 50%;
        border: solid 3px black;
        box-shadow: 10px 10px #484444;
        font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Verdana, sans-serif;
        color: #264653;
        font-size: 1.5rem;
        text-shadow: 1px 1px 2px white;
        text-align: center;
        background-color: #e9ecef;  
        padding: 15px;
    }
</style>
