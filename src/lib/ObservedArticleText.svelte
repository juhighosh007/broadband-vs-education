<script>
    import { onMount } from "svelte";

    let { children, callback, options } = $props();

    // this uniqueId just lets us target the element 
    // with `document.getElementById(uniqueId)` later on.
    // it's a little hacky, but it works. 
    let uniqueId = Math.random().toString();

    // here we define the onMount() function for this component.
    // svelte handles calling the onMount() function *after* all of the HTML in this
    // component has been mounted to the DOM. we have to put the intersection observer
    // stuff in onMount() because we need to target the <div> we create below,
    // but it won't actually exist in the DOM until it's been mounted. 
    onMount(() => {
        let intersectionObserver = new IntersectionObserver(callback, options);

        const observedElement = document.getElementById(uniqueId);
        intersectionObserver.observe(observedElement);
    });
</script>

<!-- assign the containing div the id `uniqueId` so we can target it -->
<div id={uniqueId} class="article-text">
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
