<script>
    import Scroller from "@sveltejs/svelte-scroller";
    import Back from "./BaseballBackground.svelte";
    import Anime from "./BackAnimations.svelte";
    import SideBar from "./InteractiveSide.svelte"
    import App from './WarData.svelte'

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

      <div class="progress-bars">
      <p>current section: <strong>{index + 1}/{count}</strong></p>
      <progress value={count ? (index + 1) / count : 0} />

      <p>offset in current section</p>
      <progress value={offset || 0} />

      <p>total progress</p>
      <progress value={progress || 0} />
      </div>

      <Anime {index}/>
      <Back {index} {offset}/>
    </div>

    <div class="foreground" slot="foreground" id = "foreground">
      
      <SideBar {index}/>

      <section>1</section>
      <section>2</section>
      <section>3</section>
      <section>4</section>
      <section>5</section>
      <section>6</section>
      <section>7 Batting Interactions

      </section>
      <section>8  Btting Stats</section>
      <section>9 Pitching 
    


      </section>
      <section>10 Pitching stats</section>    

      <section>11
        <h1> Bandwagoner </h1>
      </section>
      <section>

      <h1>12</h1>

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



      </section>
      <!-- Add More If needed -->
    </div>
    </Scroller>




    <style>
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
    width: 70%;
    margin: 0 auto;
    height: auto;
    position: relative;
    outline: red solid 3px;
    }

    .progress-bars {
    position: absolute;
    background: rgba(170, 51, 120, 0.2) /*  40% opaque */;
    visibility: visible;
    }

    section {
    height: 80vh;
    background-color: rgba(0, 0, 0, 0.2);
    /* 20% opaque */
    /* color: white;*/
    outline: magenta solid 3px;
    text-align: center;
    max-width: 1000px;
    /* adjust at will */
    color: black;
    padding: 1em;
    margin: 0 0 2em 0;
    }
    /* body {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
    }
    #output {
    font-family: monospace;
    }
    body {
    font-family: "Lato", sans-serif;
    } */

    .sidenav {
    height: 100%;
    width: 0;
    position: fixed;
    z-index: 1;
    top: 0;
    background-color: #016f28;
    overflow-x: hidden;
    transition: 0.5s;
    padding-top: 30px;
    padding-bottom: 30px;
    left: 0;

    }

    .sidenav a {
    padding: 8px 8px 8px 32px;
    text-decoration: none;
    font-size: 25px;
    color: #222020;
    display: block;
    transition: 0.3s;

    }

    .sidenav a:hover {
    color: #f1f1f1;
    }

    .sidenav .closebtn {
    position: absolute;
    top: 0;
    right: 25px;
    font-size: 36px;
    margin-left: 50px;
    }



    @media screen and (max-height: 450px) {
    .sidenav {padding-top: 15px;}
    .sidenav a {font-size: 18px;}
    }

    .sidenav_text{
      color:  #211f1f;
      height: 100%;
      margin: auto;
      width: 70%;
      padding: 10px;
      bottom: 10px;
    }










    </style>

