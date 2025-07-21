<script>
    let { children } = $props();
</script>

<div class="headers">
    <h1>
        {@render children()}
    </h1>
</div>

<style>
    
    .headers {
        margin: 30vh auto;
        width: 80%;
        font-family: 'Helvetica','Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Verdana, sans-serif;
        color: #264653;
        font-size: 2rem;
        text-shadow: 1px 1px 2px white;
        text-align: center;
        background-color: #f7f5eb;
        border: solid 3px black;
        padding: 15px;
        box-shadow: 10px 10px #110c0c;
    }
</style>