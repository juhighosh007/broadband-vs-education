<script>
    import Links from "../lib/Links.svelte";
</script>

<div class="container">
    <h1>HOW DOES <span class="bold">BROADBAND ACCESS</span> IMPACT <span class="bold">EDUCATIONAL ATTAINMENT</span> IN BLACK COMMUNITIES?</h1>
    <p class="name">By <Links link="https://www.linkedin.com/in/juhighsh/">Juhi Ghosh</Links> | July 2025 </p>
    <div class="texts">
        <p>We often call education the great equalizer, but what happens when <strong>access to learning</strong> itself is <span class="contrast">unequal?</span></p>
        <p>After 2020, the shift to <strong>online learning</strong> wasn't a luxury, it was a <strong>necessity</strong>. Yet millions of students were locked out, not because of academic struggle, but because their homes lacked broadband internet. And for many Black communities across the U.S., this wasn't the exception. It was the norm.
</p>
        <p>Let's take a step back.</p>
        <p>We assume broadband access is like electricity - something everyone has. But <Links link="according to All4Ed">according to All4Ed</Links>, over <span class="contrast">16.9 million</span> children in the U.S. are part of the <strong>“homework gap”</strong> - they can't complete schoolwork because they don't have internet access at home. Black, Latino, and Indigenous students are disproportionately represented in that number.</p>
        <p>This isn't just a small setback. It's part of a larger, unfair pattern that keeps opportunity out of reach.</p>
    </div>
</div>

<style>

    h1 .bold {
        font-weight: 900;
        color: #264653;
        font-family: 'Helvetica', 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Verdana, sans-serif;
    }

    h1 {
        font-size: 4rem;
        font-family: 'Helvetica', 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Verdana, sans-serif;
        text-align: center;
        color: #4e717d;
        text-shadow: 1px 1px 2px rgb(156, 168, 199);
    }

    .name {
        margin-top: -10px;
        margin-bottom: 60px;
        font-size: 25px;
        font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Verdana, sans-serif;
        text-align: center;
        color: #1c343e;
    }

    .texts {
        text-align: center;
        font-size: 25px;
        font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Verdana, sans-serif;
        padding: 0 40px;
        margin: 0 auto; 
        line-height: 1.6;
        color: #1c343e;
    }


    .container {
        background-color: #e9ecef;
        padding: 25px 25px; 
    }

    .contrast {
        font-weight: 900;
        color: #780000;
    }

</style>