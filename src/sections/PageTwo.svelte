<script>

    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

</script>

<div>
    <Scroller layout="right">
        {#snippet sticky()}
            <div>
                <p>
                    You can use Svelte to add and remove data from a Highcharts
                    chart.
                </p>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                You might notice that this basic template doesn't have certain
                features that are common in scrollytelling.
            </ArticleText>

            <ArticleText>
                For example, you might want a component that doesn't feature a
                sticky component at all. Or a component that is solely a sticky
                component.
            </ArticleText>

        {/snippet}
    </Scroller>
</div>

<style>
</style>
