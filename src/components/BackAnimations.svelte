<script>
    import { fade, draw, fly } from 'svelte/transition';
    import { tweened } from "svelte/motion";
    import { cubicOut, cubicInOut } from "svelte/easing";
    export let index;

    // const
    const base1 = tweened({ x: 670, y: 100 }, { duration: 500, easing: cubicOut });
    const base2 = tweened({ x: 670, y: 110 }, { duration: 500, easing: cubicOut });
    const base3 = tweened({ x: 670, y: 120 }, { duration: 500, easing: cubicOut });
    const homebase = tweened({ x: 670, y: 130 }, { duration: 500, easing: cubicOut });
    const pitchers_mound = tweened({ x: 670, y: 140 }, { duration: 500, easing: cubicOut });
    const coachbox = tweened({ x: 670, y: 150 }, { duration: 500, easing: cubicOut });



    $: if (index >= 1) {
        base1.set({ x: 860, y: 450 }, { duration: 1000, easing: cubicOut })
        base2.set({ x: 670, y: 270 }, { duration: 1000, easing: cubicOut });
        base3.set({ x: 500, y: 450 }, { duration: 1000, easing: cubicOut });
        homebase.set({ x: 680, y: 640 }, { duration: 1000, easing: cubicOut });
        pitchers_mound.set({ x: 665, y: 450 }, { duration: 1000, easing: cubicOut });
        coachbox.set({ x: 960, y: 520 }, { duration: 1000, easing: cubicOut });
    }


</script>

<main>
    {#if index === 0}
    <div class="first" out:fly={{ y: -20, duration: 800 }}>
        {#each 'BASEBALL' as char, i}
        <span in:fade|global={{ delay: 1000 + i * 150, duration: 800 }}>{char}</span>
        {/each}
    </div>
    <div class = "first_dumb" out:fly={{ y: -20, duration: 800 }}>
      {#each 'for dummies' as char, i}
        <span in:fade|global={{ delay: 1000 + i * 150, duration: 2000 }}>{char}</span>
        {/each}
    </div>
    <section class="header-down-arrow" out:fly={{ y: -20, duration: 800 }}>
        <img src="downarrow.png" width="50" alt="Scroll Down">
    </section>
    <div class = "names" out:fly={{ y: -20, duration: 800 }}>
        {#each 'Made By: Bill Wang & Ethan Cao' as char, i}
          <span in:fade|global={{ delay: 1000 + i * 30, duration: 2000 }}>{char}</span>
          {/each}
      </div>
    
    {/if}

    {#if index === 1}
        <div class= "explanation" out:fly={{ y: -20, duration: 800 }}>
            <span in:fade|global={{ duration: 200 }}>Baseball is a bat-and-ball game played between two teams of nine players each.
                The objective is to score runs by hitting a ball with a bat and running around a series of four bases arranged in a diamond shape.
            </span>
        </div>
    {/if}

    {#if index === 2}
        <div class="second" out:fly={{ y: -20, duration: 800 }}>
        {#each 'OutField' as char, i}
        <span in:fade|global={{ delay: 500 + i * 150, duration: 800 }}>{char}</span>
        {/each}
    </div>
    
    <div style="position: absolute; transform: translate({$base1.x}px, {$base1.y}px);">
        <span in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>first-base</span>
    </div>
    <div style="position: absolute; transform: translate({$base2.x}px, {$base2.y}px);">
        <span in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>second-base</span>
    </div>
    <div style="position: absolute; transform: translate({$base3.x}px, {$base3.y}px);">
        <span in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>third-base</span>
    </div>
    <div style="position: absolute; transform: translate({$homebase.x}px, {$homebase.y}px);">
        <span in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>homebase</span>
    </div>
    <div style="position: absolute; transform: translate({$pitchers_mound.x}px, {$pitchers_mound.y}px);">
        <span in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>pitchers-mound</span>
    </div>
    <div style="position: absolute; transform: translate({$coachbox.x}px, {$coachbox.y}px);">
        <span in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>coachbox</span>
    </div>


    <div class ='field_explanation' in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>
      <p>
        The baseball field is divided into the infield and the outfield. The infield is a square area around the home plate, where most of the action takes place. The outfield is the grassy area beyond the infield, where the outfielders position themselves.
    </p>

    
    <p>
        The game is typically played over nine innings, with each team having a turn to bat and a turn to field in each inning. The team with the most runs at the end of the nine innings is declared the winner.
    </p>
    
    </div>
    
    {/if}
    
    <!-- {#if index === 3}

    <div class ='field_explanation' in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>

    </div>


    {/if}

    {#if index === 4}
          
    {/if} -->



</main>

<style>
    @keyframes fade-slide-up {
    0% {
        opacity: 0;
        transform: translateY(4rem);
    }
    100% {
        opacity: 1;
        transform: none;
    }
    
    }
    @keyframes pulse {
    0% {
        opacity: 1;
        transform: none;
    }
    50% {
        opacity: .8;
        transform: scale(.8);
    }
    100% {
        opacity: 1;
        transform: none;
    }
    }

    .header-down-arrow {
        animation: pulse 2s 3s ease-out infinite;
        position: absolute;
        bottom: 4vh;
        left: 0;
        right: 0;
        text-align: center;
        z-index: 10;
    }
    .header-down-arrow img {
        animation: fade-slide-up 1s 1s ease-out forwards;
        opacity: 0;
    }
    .first {
        font-size: 10vw;
        position: absolute;
        right: 18%;
        top: 30%;
        /* transform: translate(-50%, -50%); */
        font-family: 'Permanent Marker';
        letter-spacing: 0.12em;
        color: #000000;
        font-weight: 600;
        font-style:normal;
    }

.first span {
    transition: opacity 0.8s ease-in-out; /* Adjust duration and easing as needed */
}

.first_dumb{
        font-size: 5vw;
        position: absolute;
        right: 10%;
        top: 50%;
        /* transform: translate(-50%, -50%); */
        font-family: 'Permanent Marker';
        letter-spacing: 0.12em;
        color: #000000;
        font-weight: 600; 
  }

.names{
    font-size: 1vw;
    position: absolute;
    right: 1%;
    top: 95%;
    /* transform: translate(-50%, -50%); */
    font-family: 'Overpass';
    letter-spacing: 0.12em;
    color: #000000;
    font-weight: 400; 
}

.second {
        font-size: 2vw;
        position: absolute;
        right:45%;
        top: 10%;
        /* transform: translate(-50%, -50%); */
        font-family: 'Overpass';
        letter-spacing: 0.12em;
        color: #000000;
        font-weight: 400; 
}

/* .first_base {
    font-size: 2vw;
    right:25%;
    top: 60%;
    position: absolute;
} */

.explanation{
    font-size: 2vw;
    position: absolute;
    right: 30%;
    left : 30%;
    top: 30%;
        /* transform: translate(-50%, -50%); */
    font-family: 'Overpass';
    letter-spacing: 0.12em;
    color: #000000;
    font-weight: 400;

}
.field_explanation {
      position: absolute;
      background: rgba(170, 51, 120, 0.2); /* 40% opaque */
      visibility: visible;
      position: fixed;
      right: 5%; /* Adjust the left value as needed */
      bottom: 5%; /* Adjust the bottom value as needed */
      z-index: 1; /* Ensure the div appears on top of other elements */
      width: 250px; /* Adjust this value to your desired width */
      padding: 10px; /* Add some padding for spacing between the content and the div's edges */
      box-sizing: border-box; 
  }

</style>