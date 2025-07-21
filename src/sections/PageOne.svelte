<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ObservedArticleText from "../lib/ObservedArticleText.svelte";

    // this `options` object below is passed into the <ObservedArticleText>
    // component, and from there it gets passed to the IntersectionObserver object w
    // when it's created.
    // the thresholds to fire the callback are 85% and 95%. in the callback function,
    // we check whether the visible area is >= 90%. so, triggering the callback at
    // 85% and 95% ensures we trigger the correct change in background color
    // whether the element is being scrolled into the viewport or out of the viewport.
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

    let chartOptions = {
chart: {
    type: 'bar',
    style: {
      fontFamily: 'Helvetica'
    },
    backgroundColor: '#fff'},

colors: ['#5b8dee', '#2A9D8F'],
  
title: {
    text: 'Broadband vs Education Data (2023)',
    style: {
      fontFamily: 'Helvetica, sans-serif',
      fontSize: '14px',
      color: '#264653'
    },
  },
xAxis: {
    categories: ["Prince George's County, Maryland", "Issaquena County, Mississippi", "Henry County, Georgia", "Claiborne Parish, Louisiana"]
},
yAxis: {
    min: 0,
    max: 100,
    title: {
      text: 'Percentage (%)'
    }
  },
tooltip: {
    valueSuffix: ' %'
  },
plotOptions: {
    bar: {
      dataLabels: {
        enabled: true
      },
      groupPadding: 0.1
    }
  },
legend: {
    reversed: false
  },
credits: {
    enabled: false
  },
series: [
    {
      name: 'Black Households with Broadband Access',
      data: [94.6, 48.7, 95.8, 41.8]
    },
    {
      name: "Bachelor's Degree or Higher Attainment among Black Residents",
      data: [37.1, 2.2, 32.1, 4.6]
    }
  ]
};


</script>

<div class="container">
    <Scroller layout="left">
        {#snippet sticky()}
            <div class="chart">
                <Chart options={chartOptions} highcharts={Highcharts} />
            </div>
            <div class="texts">
                <p>The chart above compares broadband access and bachelor's degree attainment among Black households in selected U.S. counties.</p>
                <p>The disparities are stark - counties with lower internet access often show lower educational outcomes too, reflecting how digital infrastructure and education are deeply intertwined.</p>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ObservedArticleText {callback} {options}>
                To truly grasp the impact, take a look at the data on the right.
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                <p>In Prince George's, <span class="highlight">94.6%</span> of Black households have broadband.</p>
                <p>It's one of the <strong>best-connected</strong> Black-majority counties in the U.S.</p>
                <p>Their graduation rate? <span class="highlight">37.1%</span>.</p>

            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                <p>Issaquena County: only <span class="contrast">48.7%</span> of Black households have broadband.</p>
                <p>That means <em>nearly half</em> of Black families are <strong>offline</strong>.</p>
                <p>Graduation rate? Just <span class="contrast">2.2%</span>.</p>

            </ObservedArticleText>
            
            <ObservedArticleText {callback} {options}>
                <p>This digital divide doesn't just block Netflix.</p>
                <p>It blocks college applications, online tutoring, job training, basic research, and even the ability to show up in a remote class.</p> 
            </ObservedArticleText>

            <ObservedArticleText {callback} {options}>
                Some call it an infrastructure issue. But it's also a civil rights issue.
            </ObservedArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .chart {
        width: 90%;
        height: 400px;
        margin: 0px auto;
        border: solid 3px #264653;
    }

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