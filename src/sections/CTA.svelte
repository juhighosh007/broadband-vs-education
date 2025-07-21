<script>
import Headers from "../lib/Headers.svelte";
import Links from "../lib/Links.svelte";
import Scroll from "../lib/Scroll.svelte";
</script>

<div>
    <Scroll backgroundImage="https://images.pexels.com/photos/2246258/pexels-photo-2246258.jpeg">
        {#snippet scrolly()}
            <Headers>
                <span class="contrast">CLOSE THE GAP</span>
            </Headers>

            <Headers>
                <span class="contrast">Donate to Digital Inclusion</span>
                <p><em>Support organizations bridging the broadband gap in Black and rural communities.</em></p>
                <p><Links link="https://www.digitalinclusion.org/donate/">National Digital Inclusion Alliance</Links> - funds training, devices & internet access for underserved areas</p>
            </Headers>

            <Headers>
                <span class="contrast">Help Connect a Family</span>
                <p><em>Don’t let cost keep someone offline.</em></p>
                <p><Links link="https://www.everyoneon.org/">EveryoneOn</Links> helps low-income households get affordable broadband and devices.</p>
            </Headers>

            <Headers>
                <span class="contrast">Get Involved - Teach Digital Skills</span>
                <p><em>You can help bridge the digital divide in your community.</em></p>
                <p>Volunteer as a Digital Navigator with the <Links link="https://digitalequitycenter.org/join-us/ndec-volunteer-digital-navigator-program/">National Digital Equity Center</Links> - you’ll be matched with individuals or families who need support getting online.</p>
            </Headers>

        {/snippet}
    </Scroll>
</div>

<style>
    .contrast {
        font-weight: 900;
        color: #780000;
    }

    p {
        font-size: 25px;
    }

    .highlight {
        font-weight: 900;
        color: #283618;
    }    
</style>