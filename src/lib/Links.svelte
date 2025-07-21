<script>
    let { children, link } = $props();
</script>

<a class="links" href={link} target="_blank">
        {@render children()}
</a>

<style>
    a:link {
        color: #264653;
    }

    a:visited {
        color: #3c096c;
    }

    a:hover {
        color: #4f000b;
    }

</style>