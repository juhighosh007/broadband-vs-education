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
    <Scroller layout="left">
        {#snippet sticky()}
            <div>
                <img src="https://images.pexels.com/photos/3280130/pexels-photo-3280130.jpeg" alt="hand cheer"> 
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ObservedArticleText {callback} {options}>
                <p>With students sent home and systems unprepared, neighbors, grandmothers, and bookstore owners did what the broadband giants couldn’t - <em>they connected the disconnected.</em></p>
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                <p>When schools closed in March 2020, the assumption was that learning would simply move online. But along the poverty-scarred stretch of I-95, especially across Black and rural communities, it wasn’t that easy.
</p>
            </ObservedArticleText>
            <ObservedArticleText {callback} {options}>
                <p>Broadband didn’t exist in many homes. Devices were missing. Phone data ran out. The digital divide - long warned about - became a <strong>full-blown rupture.</strong>
            </ObservedArticleText>
            <ObservedArticleText {callback} {options}>
                <p><em>“I was on LinkedIn and everything, begging people for laptops. It was horrible,”</em> said Pickett, a local resident who didn’t wait for a government fix. She <span class="contrast">turned her own WiFi hotspot into a neighborhood signal</span>, so nearby children could keep up with school.</p>
            </ObservedArticleText>
           
        {/snippet}
    </Scroller>

    <Scroller layout="right">
        {#snippet sticky()}
            <div>
                <img src="https://images.pexels.com/photos/11025019/pexels-photo-11025019.jpeg" alt="children infront of a laptop"> 
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ObservedArticleText {callback} {options}>
                <p>Down in Beaufort County, South Carolina, 79-year-old Esther Shaver-Harnett didn’t wait for solutions. She created her own.</p>
            
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                <p>A retired bookstore owner with no formal background in tech, Esther <span class="contrast">personally purchased 100 mobile hotspots</span> for children in her community - because, as she put it, <em>“no one else was doing it.”</em></p>
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                <p><em>“I’ve started raising hell, not money yet,”</em> she added, as her grassroots campaign to bring the internet to low-income students grew in urgency after the pandemic hit. In her eyes, this wasn’t just about broadband. It was about justice.</p>
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                <p>These stories underscore what’s at stake when internet access is treated as optional - and who picks up the slack when institutions fall short.</p>
                <p>They also hint at what’s possible: when one woman arms her town with hotspots, or when a single hotspot powers an entire neighborhood’s dreams, the infrastructure may be invisible - but its impact is undeniable.</p>
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                <p>All stories and interviews referenced in this article are drawn from <Links link="https://www.context.news/socioeconomic-inclusion/long-read/black-and-rural-students-left-behind-as-us-schools-go-online">Context News</Links>.</p>
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


    .container {
        background-color: #f7f5eb;
        padding: 25px 25px;
    }

    p {
        font-size: 25px;
    }

img {
    width: 100%;
    margin: 0px auto;
    border: 3px solid #264653;
    padding: 10px;
    border-radius: 20px;
}
</style>