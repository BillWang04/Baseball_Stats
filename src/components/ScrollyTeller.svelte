<script>
    import Scroller from "@sveltejs/svelte-scroller";
    import Back from "./BaseballBackground.svelte";
    import Anime from "./BackAnimations.svelte";
    import SideBar from "./InteractiveSide.svelte";
    import { fade, fly } from 'svelte/transition';
    let count, index, offset, progress;


</script>

    <Scroller
    top={0.0}
    bottom={1}
    threshold={0.5}
    bind:count
    bind:index
    bind:offset
    bind:progress
    >
    <div class="background" slot="background" id = "background">
      <!-- <div class ="offset">
        <p>offset in current section</p>
        <progress value={offset || 0} />
      </div>


      <div class="progress-bars">
      <p>current section: <strong>{index + 1}/{count}</strong></p>
      <progress value={count ? (index + 1) / count : 0} />

      <p>total progress</p>
      <progress value={progress || 0} />
      </div> -->

      <Anime {index}/>
      <Back {index} {offset}/>
    </div>

    <div class="foreground" slot="foreground" id = "foreground">
      
      <SideBar {index}/>

      <section>
        {#if index === 0}
        <div in:fade|global={{ delay: 1000, duration: 2000 }} out:fly={{ y: -20, duration: 800 }} class="button-container">
          <div class="buttons" onclick="location.href='./test'">Explore WAA</div>
          <div class="buttons" onclick="location.href='./writeup'">Write-Up</div >
          <div class="buttons" onclick="location.href='https://youtu.be/1SelsiPbrm8'">Video</div>
        </div>
        {/if}
      </section> <!-- 1-->
      <section/> <!-- 2-->
      <section/> <!-- 3-->
      <section/> <!-- 4 (sidebar)-->
      <section/><!-- 5-->
      <section/><!-- 6-->
      <section> <!-- 7--></section>
      <section></section> <!-- 8-->
      <section/><!-- 9-->
      <section/><!-- 10-->
      <section/><!-- 11-->
      <section>


          <button onclick="playBall()">Play Ball!</button>
          <div id="output_game"></div>

          <script>
          function playBall() {
              const outputElement = document.getElementById('output_game');
              outputElement.innerHTML = ''; // Clear previous output

              // Simulate a baseball game
              const innings = 9;
              let homeScore = 0;
              let awayScore = 0;

              for (let inning = 1; inning <= innings; inning++) {
                  const homeRuns = Math.floor(Math.random() * 4);
                  const awayRuns = Math.floor(Math.random() * 4);

                  homeScore += homeRuns;
                  awayScore += awayRuns;

                  outputElement.innerHTML += `Inning ${inning}: Home ${homeRuns} - ${awayRuns} Away<br>`;
              }

              outputElement.innerHTML += '<strong>Final Score:</strong><br>';
              outputElement.innerHTML += `Home: ${homeScore} - Away: ${awayScore}<br>`;

              if (homeScore > awayScore) {
                  outputElement.innerHTML += '<strong>Home team wins!</strong>';
              } else if (awayScore > homeScore) {
                  outputElement.innerHTML += '<strong>Away team wins!</strong>';
              } else {
                  outputElement.innerHTML += '<strong>It\'s a tie!</strong>';
              }
          }
          </script>

        <div class = "text_descript">
          <p>
            After exploring our project, we hope that you have a better understanding of how baseball and its statistics work. Our project was tailor-made to help beginners understand how baseball works in an interactive way. Now, use your knowledge to analyze the graphs in our Explore WAA section. Click on the yellow boxes to zoom in and interact with the graphs. Then click on the field to zoom out. Have fun! 
          </p>

        </div>


        <div class="buttons" style="margin: 0 auto;" onclick="location.href='./test'">Explore WAA</div>


      </section>
      <!-- Add More If needed -->
    </div>
    </Scroller>




    <style>
    .button-container {
      display: flex;
      flex-direction: row-reverse;
      z-index: 100;
    }

    .buttons {
      height: 7vh;
      width: 10vw;
      border: 2px solid #422800;
      border-radius: 3vw;
      box-shadow: #422800 4px 4px 0 0;
      color: #422800;
      background-color: #fbeee0;
      cursor: pointer;
      font-weight: 600;
      font-size: 18px;
      text-align: center;
      border-radius: 2vh;
      line-height: 6vh;
      margin: 1vh 1.5vw 0px 1.5vw;
      z-index: 100;
      transition: background-color 0.5s; 
    }

    .buttons:hover {
      background-color: white;
    }
    .background {
    width: 650px; /* Set the desired width for your SVG */
    height: 500px; /* Set the desired height for your SVG */
    width: 100%;
    height: 100vh;
    position: relative;
    outline: green solid 3px;
    background-color: #00a83b;
    }

    .foreground {
    width: 100%;
    margin: 0 auto;
    height: auto;
    position: relative;
    /* outline: red solid 3px; */
    }

    /* .progress-bars {
    position: absolute;
    background: rgba(170, 51, 120, 0.2);
    visibility: hidden;
    } */

    section {
    height: 200vh;
    /* background-color: rgba(0, 0, 0, 0.2); */
    /* 20% opaque */
    /* color: blue; */
    /* outline: magenta solid 3px; */
    text-align: center;
    max-width: 150%;
    /* adjust at will */
    color: black;
    padding: 1em;
    margin: 0 0 2em 0;
    }
    .text_descript {
      background: rgba(232, 195, 216, 0.2); /* 40% opaque */
      visibility: visible;
      /* margin-top: 15%; */
      margin-left: 25%;
      z-index: 1; /* Ensure the div appears on top of other elements */
      width: 50%; /*Adjust this value to your desired width */
      padding: 10px; /* Add some padding for spacing between the content and the div's edges */
      box-sizing: border-box; 
      font-size: 24;
  }
  
    </style>

