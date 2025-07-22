<script>
  import { afterUpdate } from "svelte";
    import Headers from "../lib/Headers.svelte";
    import Scroll from "../lib/Scroll.svelte";
    let button1Text = "Wait until school tomorrow";
    let button2Text = "Use your phone’s hotspot (data capped)";
    let button3Text = "Drive 30 minutes to a library parking lot with Wi-Fi";
    let Text="It’s 10:00 PM. You have a history paper due by midnight. You don’t have broadband at home.";
    let currentScene=0;
    let score=0;
    let finalText = "";
    let showConsequence = false;
    let consequenceText = "";
 
    const scenarios = [
    {
      name: "scene 1",
      text: "It’s 10:00 PM. You have a history paper due by midnight. You don’t have broadband at home.",
      choices: [
        {
          label: "Wait until school tomorrow",
          consequence: "Missed submission → Grade drops",
          score: 0
        },
        {
          label: "Use your phone’s hotspot (data capped)",
          consequence: "Slow typing, lag → Quality suffers",
          score: 1
        },
        {
          label: "Drive 30 minutes to a library parking lot with Wi-Fi",
          consequence: "Exhausted, unsafe late at night → Stress builds",
          score: 2
        }
      ]
    },
    {
      name: "scene 2",
      text: "Today is the deadline for submitting your FAFSA and college application. The websites won’t load on your phone.",
      choices: [
        {
          label: "Skip it — you’ll try next year",
          consequence: "Missed opportunity → Delay in goals",
          score: 0
        },
        {
          label: "Ask your neighbor for Wi-Fi",
          consequence: "Awkward + insecure connection",
          score: 1
        },
        {
          label: "Stay after school to use lab internet",
          consequence: "Alone in school after hours → Stress + risk",
          score: 2
        }
      ]
    },
    {
      name: "scene 3",
      text: "You’re assigned to present on Zoom during your virtual class. Your connection is unstable.",
      choices: [
        {
          label: "Turn off your camera + mic to save bandwidth",
          consequence: "Teacher marks you absent",
          score: 1
        },
        {
          label: "Drop the call and email your teacher later",
          consequence: "Lose confidence, fall behind",
          score: 0
        },
        {
          label: "Message classmate to present your slides for you",
          consequence: "Depend on peers → Limited learning",
          score: 2
        }
      ]
    },
    {
      name: "scene 4",
      text: "Your math final is online — 90 minutes, no re-entry allowed. You’ve lost connection twice this week already.",
      choices: [
        {
          label: "Take the risk on your phone",
          consequence: "Lag causes you to miss questions",
          score: 0
        },
        {
          label: "Ask for a paper-based version (may be denied)",
          consequence: "Denied request → zero score",
          score: 1
        },
        {
          label: "Ask teacher to reschedule or take in school lab",
          consequence: "Extra pressure + anxiety → outcome varies",
          score: 2
        }
      ]
    }
  ];

  function handleChoice(index) {
    const current = scenarios[currentScene];
    const choice = current.choices[index];

    score += choice.score;
    consequenceText = choice.consequence;
    showConsequence = true;

    setTimeout(() => {
      showConsequence = false;
      currentScene += 1;

      if (currentScene >= scenarios.length) {
        calculateFinalText();
      }
    }, 1500);
  }

  function restart() {
    score = 0;
    currentScene = 0;
    finalText = "";
    showConsequence = false;
    consequenceText = "";
  }
  
  function calculateFinalText() {
    let message = "";
    let percent = 0;

    if (score <= 2) {
      percent = 37;
      message = "Severely limited by lack of access.";
    } else if (score <= 4) {
      percent = 63;
      message = "You made it through, but at a cost.";
    } else if (score <= 6) {
      percent = 75;
      message = "You navigated the gaps with effort.";
    } else {
      percent = 88;
      message = "You overcame the odds — barely.";
    }

    finalText = `Simulation Complete: Could You Graduate Without Internet?<br>
Your Graduation Likelihood: ${percent}%.<br>
${message}<br>
Compare with: Students with stable broadband access: 93%`;
  }

</script>

<div class="container">
    <Scroll>
        {#snippet scrolly()}
            <Headers>
                <span class="contrast">Can You Graduate Without Internet?</span>
            </Headers>
            <Headers>
                <p class="desc">You’re a Black high school student in a low-broadband county. You’ll face 4 real-life situations where access to the internet can impact your education. Your choices determine your graduation chance.</p>
            </Headers>
        {/snippet}
    </Scroll>

    <Scroll>
    {#snippet scrolly()}
      <Headers>
  {#if currentScene < scenarios.length}
    <div class="game">

      {#if !showConsequence}
        <div class="controls">
          {#each scenarios[currentScene].choices as choice, i}
            <button on:click={() => handleChoice(i)}>
              {choice.label}
            </button>
          {/each}
        </div>
      {/if}

      <div class="text">
        <p>{scenarios[currentScene].text}</p>
      </div>

      {#if showConsequence}
        <p class="consequence">{consequenceText}</p>
      {/if}

    </div>
  {:else}
    <div class="final">
      <p>{@html finalText}</p>
      <button on:click={restart}>Replay?</button>
    </div>
  {/if}
</Headers>

    {/snippet}

    </Scroll>
</div>

<style>
    button {
        cursor: pointer;
        color: white;
        background-color: #2a9d8f;
        background-image: linear-gradient(#2a9d8f, #45b1a4)
        border: 3px solid #2a9d8f;
        font-weight: bold;
        font-family: 'Helvetica','Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Verdana, sans-serif;
        font-size: 1.5rem;
        padding: 20px 20px;
    } 

    .game {
        max-width: 1100px;
        max-height: 800px;
        margin: 30px auto;
        padding: 10px;
        background-color: #e9ecef;
        border: 3px solid #264653;
    }

    .text, .final {
        padding: 20px 40px;
        text-align: center;
        font-size: 1.5rem;
        font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Verdana, sans-serif;
        color: #1c343e;
    }

    .consequence {
        font-size: 40px; 
        line-height: 1.4;
        font-weight: 900;
        color: #780000;
    }

    .container {
        background-color: #e9ecef;
        padding: 25px 25px;
    }

    .contrast {
        font-weight: 900;
        color: #780000;
    }

    .desc {
        font-size: 30px;
    }
</style>