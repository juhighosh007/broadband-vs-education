<script>
    import Links from "../lib/Links.svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ObservedArticleText from "../lib/ObservedArticleText.svelte";

     const options = {
        threshold: [0.85, 0.95],
    };

    const callback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;

            if (entry.intersectionRatio >= 0.9) {
                // "active" state
                elem.style.backgroundColor = "#e9ecef";
            } else if (entry.intersectionRatio < 0.9) {
                // "inactive" state
                elem.style.backgroundColor = "#888888";
            }
        });
    };

</script>

<div class=container>
    <Scroller layout="right">
        {#snippet sticky()}
        <div style="width: 100%;">
            <iframe title="ScatterPlot" src="/broadband-vs-education/scatterPlot.html" width="100%" height="500" style="border: 2px solid #ccc; border-radius: 8px;"></iframe>
        </div>
            <div class="texts">
                <p>
                    Each point represents a county, comparing broadband access in Black households (%) to the share of Black residents with a bachelor’s degree or higher.
                </p>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ObservedArticleText {callback} {options}>
                To the left, a scatterplot shows 2023 data from U.S. counties with high Black populations. 
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                In 2025, the stakes are even <span class="contrast">higher</span>. As <Links link="https://www.emergingtechbrew.com/stories/2025/01/14/black-communities-internet-access-pollution?__cf_chl_rt_tk=j_7SLaZo6oBXw85Hp4kKk6EDz_4XJyuD2kYwlw_xcWQ-1753081174-1.0.1.1-7fYgeeZzGCXx1kCI2i.w3TW0G1fr5HvBKs8IcYjkGwE">Emerging Tech Brew</Links> reports, <strong>digital pollution</strong> - like <em>slow speeds, unreliable connections,</em> and <em>bandwidth caps</em> - is <strong>quietly hurting Black communities</strong>, especially in urban areas where broadband infrastructure is aging and under-maintained.
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                <p>And in rural areas, it’s <em>even worse</em>. According to <Links link="https://www.context.news/socioeconomic-inclusion/long-read/black-and-rural-students-left-behind-as-us-schools-go-online">Context News</Links>, nearly <span class="contrast">1 in 3</span> Black American students lacks a home internet connection - compared to just <span class="highlight">1 in 5</span> white students.
                <p>Many rural schools serving Black students had <strong>no plan at all</strong> for online access during remote learning. <em>Is that what education access looks like?</em></p>
            </ObservedArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .contrast {
        font-weight: 900;
        color: #780000;
    }

    .highlight {
        font-weight: 900;
        color: #283618;
    }

    .texts {
        padding: 10px 40px;
        text-align: center;
        font-size: 1rem;
        font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Verdana, sans-serif;
        color: #1c343e;
    }

    .container {
        background-color: #f7f5eb;
        padding: 25px 25px;
    }

</style>
