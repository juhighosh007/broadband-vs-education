<script>
    import Headers from "../lib/Headers.svelte";
    import Scroll from "../lib/Scroll.svelte";
</script>

<div>
    <Scroll backgroundImage="https://images.pexels.com/photos/30973503/pexels-photo-30973503.jpeg">
        {#snippet scrolly()}
            <Headers>
                What happens when your classroom is out of reach?
            </Headers>

            <Headers>
                When lectures buffer, assignments lag, and futures stall?
            </Headers>
        {/snippet}
    </Scroll>
    <Scroll backgroundImage="https://images.pexels.com/photos/13189196/pexels-photo-13189196.jpeg">
        {#snippet scrolly()}
        <Headers>
                No Wi-Fi? 
            </Headers>

            <Headers>
                No degree.
            </Headers>
            <Headers>
                For thousands of Black students across the U.S., this <span class="contrast">isn't</span> an exaggeration
            </Headers>
        {/snippet}
    </Scroll>
    <Scroll backgroundImage="https://images.pexels.com/photos/259269/pexels-photo-259269.jpeg">
        {#snippet scrolly()}
            <Headers>
                It's their <span class="contrast"><em>REALITY</em></span>
            </Headers>

            <Headers>
                In Claiborne Parish, Louisiana, just <span class="contrast">4.6%</span> of Black residents hold a <span class="highlight">bachelor's degree</span>
            </Headers>

            <Headers>
                And only <span class="contrast">41.8%</span> have <span class="highlight">reliable internet</span> to even try
            </Headers>
        {/snippet}
    </Scroll>
</div>

<style>
    .contrast {
        color: #780000;
    }

    .highlight {
        color: #000000;
    }
</style>