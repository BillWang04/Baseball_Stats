<script>
    import Scroller from "@sveltejs/svelte-scroller";
    import App from "./App.svelte" 
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
  <div class="background" slot="background">

    <div class="progress-bars">
      <p>current section: <strong>{index + 1}/{count}</strong></p>
      <progress value={count ? (index + 1) / count : 0} />

      <p>offset in current section</p>
      <progress value={offset || 0} />

      <p>total progress</p>
      <progress value={progress || 0} />
    </div>

    <svg width="100%" height="100%" id="svg2" viewBox="0 0 650 500">

      <g id="layer1">
        <path id="field" d="M 150,500 L 0,500 L 0,0 L 650,0 L 650,500 L 508,500 L 150,500 z "/>
        <path id="infield-dirt" d="M 205,752.36218 A 95,95 0 0 1 395,752.36218" transform="matrix(1.989102,0,0,1.978205,-268.2308,-1169.879)"/>
        <path id="hide-dirt-right" d="M 328.5,439.48263 L 538.5,229.48266 L 538.5,439.48263 L 328.5,439.48263 z "/>
        <path id="hide-dirt-left" d="M 328.5,439.48263 L 124.5,235.48266 L 123.5,439.48263 L 328.5,439.48263 z "/>
        <rect id="hide-dirt-top" width="168.31494" height="168.31494" x="-77.781464" y="374.03622" transform="matrix(0.707107,-0.707107,0.707107,0.707107,0,0)"/>
        <path id="batter-box-dirt" d="M 371 430 A 43 43 0 1 1  285,430 A 43 43 0 1 1  371 430 z"/>
        <path id="pitchers-mound" d="M 318 752.36218 A 18 18 0 1 1  282,752.36218 A 18 18 0 1 1  318 752.36218 z" transform="translate(28.5,-432.8794)"/>
        <path id="right-baseline" d="M 363.00993,405 C 650.37706,117.62236 650.37706,117.62236 650.37706,117.62236"/>
        <path id="left-baseline" d="M 293.77042,404.99993 C -2.1085256,109.12113 -2.1085256,109.12113 -2.1085256,109.12113"/>
        <rect id="third-base" width="10.242649" height="10.242649" x="369.26904" y="66.99128" transform="matrix(0.707107,0.707107,-0.707107,0.707107,0,0)"/>
        <rect id="first-base" width="10.242652" height="10.242652" x="531.56042" y="-95.300102" transform="matrix(0.707107,0.707107,-0.707107,0.707107,0,0)"/>
        <rect id="second-base" width="10.242655" height="10.242655" x="369.26904" y="-95.643242" transform="matrix(0.707107,0.707107,-0.707107,0.707107,0,0)"/>
        <rect id="pitchers-mound-bump" width="14" height="4" x="321.5" y="317.4827"/>
        <path id="home-plate" d="M 320,423 L 335,423 L 335,430.7492 L 327.72761,438 L 320,429.78055 L 320,423 z "/>
        <rect id="right-batter-box" width="15" height="35" x="340" y="410"/>
        <rect id="left-batter-box" width="15" height="35" x="300" y="410"/>
        <rect id="catcher-box" width="15.150455" height="25.009609" x="319.92477" y="442.5"/>
        <rect id="third-coach-box" width="10.000003" height="25.000008" x="-109.12236" y="360.85239" transform="matrix(0.707107,-0.707107,0.707107,0.707107,0,0)"/>
        <rect id="first-coach-box" width="10.000017" height="25.000046" x="-574.22095" y="78.894386" transform="matrix(-0.707107,-0.707107,0.707107,-0.707107,0,0)"/>
        <path id="left-on-deck" d="M 235 457.5 A 12.5 12.5 0 1 1  210,457.5 A 12.5 12.5 0 1 1  235 457.5 z"/>
        <path id="right-on-deck" d="M 235 457.5 A 12.5 12.5 0 1 1  210,457.5 A 12.5 12.5 0 1 1  235 457.5 z" transform="translate(209.5,0.5)"/>
        <path id="home-dirt-border" d="M 295,405 C 295.15103,402.74278 293.1875,403.97917 292.28125,403.46875 C 280.62645,419.16193 280.35712,439.683 291.625,455.65625 C 305.77503,475.71519 333.59731,480.52502 353.65625,466.375 C 373.71519,452.22497 378.52502,424.40269 364.375,404.34375 L 361,405 C 362.65625,407.375 361,405 362.65625,407.375 L 293.875,406.53125 L 295,405 z M 293.875,406.53125 L 362.65625,407.375 C 374.80016,425.99135 370.24983,450.98832 351.9375,463.90625 C 333.20494,477.12061 307.30812,472.67006 294.09375,453.9375 C 283.82751,439.38417 283.83997,421.05606 293.875,406.53125 z "/>
      </g>
    </svg>



      <!-- <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <circle cx = 12 cy = 12 r =12/>
        Add other SVG elements as needed
    </svg> -->
    

  </div>

  <div class="foreground" slot="foreground">
    <section>
      <h1>BaseBall For Dummies</h1>

      <p> Baseball is a bat-and-ball sport played between two teams, each consisting of nine players. It is widely regarded as America's pastime, with a rich history and cultural significance. The game is played on a diamond-shaped field with four bases arranged in a square: first base, second base, third base, and home plate.</p>

    <h2>Objective:</h2> 

      <p> The primary objective of baseball is for a team to score more runs than its opponent. A run is scored when a player successfully rounds all four bases and reaches home plate after hitting a pitched ball.</p>
    
    <h2>Gameplay:</h2>

      <p><strong>Innings:</strong> A standard baseball game is divided into nine innings. Each inning consists of two halves: the top half and the bottom half. In the top half, one team plays defense, and the other plays offense. The roles switch in the bottom half.</p>

      <p><strong>Teams:</strong> The defensive team comprises a pitcher, catcher, four infielders (first baseman, second baseman, shortstop, and third baseman), and three outfielders (left fielder, center fielder, and right fielder). The offensive team sends its players to bat in a specific order.</p>

      <p><strong>Pitching:</strong> The game begins with a pitcher from the defensive team throwing pitches to a batter from the offensive team. The batter's goal is to hit the pitched ball into the field of play.</p>

      <p><strong>Hitting:</strong> A batter can hit the ball and attempt to reach base. Bases are reached in order: first, second, third, and home. A hit that allows the batter to reach first base is called a single, second base a double, third base a triple, and reaching home plate is a home run.</p>

      <p><strong>Fielding:</strong> The defensive team aims to prevent the offensive team from scoring by fielding the ball and making outs. Fielders attempt to catch or retrieve the batted ball and throw it to their teammates at the bases.</p>

      <p><strong>Outs:</strong> Outs are recorded in various ways, such as striking out a batter, catching a hit ball before it touches the ground, or tagging a baserunner with the ball. When a team records three outs, their turn to bat or field ends, and the teams switch roles.</p>

      <p><strong>Scoring:</strong> Runs are scored when a baserunner successfully circles all four bases and reaches home plate. The team with the most runs at the end of nine innings wins the game.</p>

      <h2>Additional Rules and Strategies:</h2>

      <ul>
          <li><strong>Base on Balls (Walk):</strong> If a pitcher throws four balls outside the strike zone, the batter is awarded first base.</li>
          <li><strong>Strikeout:</strong> When a batter accumulates three strikes, either by swinging and missing or looking at called strikes, they are out.</li>
          <li><strong>Stealing Bases:</strong> Runners can attempt to steal bases during the pitcher's delivery to the plate.</li>
          <li><strong>Substitutions:</strong> Teams can make substitutions during the game, bringing in relief pitchers, pinch hitters, or defensive specialists.</li>
      </ul>

      <p>Baseball's combination of skill, strategy, and athleticism, along with its timeless traditions, has made it a beloved sport enjoyed by millions worldwide. The game's strategic nuances, memorable moments, and sense of tradition contribute to its enduring popularity.</p>



    </section>

    <section>
      <!-- <h1>Some type of Animation about the game point at the bases when scrolling</h1> -->
    </section>

    <section>
        <h2>This is the third section.</h2>
        

    </section>


    <section>This is the fourth section.</section>

    <section>
    <h1>This is the fifth section.</h1>

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




<div class="field-container">
  <svg width="1000" height= "800"id="svg2" viewBox="0 0 650 500">

    <g id="layer1">
      <path id="field" d="M 150,500 L 0,500 L 0,0 L 650,0 L 650,500 L 508,500 L 150,500 z "/>
      <path id="infield-dirt" d="M 205,752.36218 A 95,95 0 0 1 395,752.36218" transform="matrix(1.989102,0,0,1.978205,-268.2308,-1169.879)"/>
      <path id="hide-dirt-right" d="M 328.5,439.48263 L 538.5,229.48266 L 538.5,439.48263 L 328.5,439.48263 z "/>
      <path id="hide-dirt-left" d="M 328.5,439.48263 L 124.5,235.48266 L 123.5,439.48263 L 328.5,439.48263 z "/>
      <rect id="hide-dirt-top" width="168.31494" height="168.31494" x="-77.781464" y="374.03622" transform="matrix(0.707107,-0.707107,0.707107,0.707107,0,0)"/>
      <path id="batter-box-dirt" d="M 371 430 A 43 43 0 1 1  285,430 A 43 43 0 1 1  371 430 z"/>
      <path id="pitchers-mound" d="M 318 752.36218 A 18 18 0 1 1  282,752.36218 A 18 18 0 1 1  318 752.36218 z" transform="translate(28.5,-432.8794)"/>
      <path id="right-baseline" d="M 363.00993,405 C 650.37706,117.62236 650.37706,117.62236 650.37706,117.62236"/>
      <path id="left-baseline" d="M 293.77042,404.99993 C -2.1085256,109.12113 -2.1085256,109.12113 -2.1085256,109.12113"/>
      <rect id="third-base" width="10.242649" height="10.242649" x="369.26904" y="66.99128" transform="matrix(0.707107,0.707107,-0.707107,0.707107,0,0)"/>
      <rect id="first-base" width="10.242652" height="10.242652" x="531.56042" y="-95.300102" transform="matrix(0.707107,0.707107,-0.707107,0.707107,0,0)"/>
      <rect id="second-base" width="10.242655" height="10.242655" x="369.26904" y="-95.643242" transform="matrix(0.707107,0.707107,-0.707107,0.707107,0,0)"/>
      <rect id="pitchers-mound-bump" width="14" height="4" x="321.5" y="317.4827"/>
      <path id="home-plate" d="M 320,423 L 335,423 L 335,430.7492 L 327.72761,438 L 320,429.78055 L 320,423 z "/>
      <rect id="right-batter-box" width="15" height="35" x="340" y="410"/>
      <rect id="left-batter-box" width="15" height="35" x="300" y="410"/>
      <rect id="catcher-box" width="15.150455" height="25.009609" x="319.92477" y="442.5"/>
      <rect id="third-coach-box" width="10.000003" height="25.000008" x="-109.12236" y="360.85239" transform="matrix(0.707107,-0.707107,0.707107,0.707107,0,0)"/>
      <rect id="first-coach-box" width="10.000017" height="25.000046" x="-574.22095" y="78.894386" transform="matrix(-0.707107,-0.707107,0.707107,-0.707107,0,0)"/>
      <path id="left-on-deck" d="M 235 457.5 A 12.5 12.5 0 1 1  210,457.5 A 12.5 12.5 0 1 1  235 457.5 z"/>
      <path id="right-on-deck" d="M 235 457.5 A 12.5 12.5 0 1 1  210,457.5 A 12.5 12.5 0 1 1  235 457.5 z" transform="translate(209.5,0.5)"/>
      <path id="home-dirt-border" d="M 295,405 C 295.15103,402.74278 293.1875,403.97917 292.28125,403.46875 C 280.62645,419.16193 280.35712,439.683 291.625,455.65625 C 305.77503,475.71519 333.59731,480.52502 353.65625,466.375 C 373.71519,452.22497 378.52502,424.40269 364.375,404.34375 L 361,405 C 362.65625,407.375 361,405 362.65625,407.375 L 293.875,406.53125 L 295,405 z M 293.875,406.53125 L 362.65625,407.375 C 374.80016,425.99135 370.24983,450.98832 351.9375,463.90625 C 333.20494,477.12061 307.30812,472.67006 294.09375,453.9375 C 283.82751,439.38417 283.83997,421.05606 293.875,406.53125 z "/>
    </g>
  </svg>
</div>


<style>
  #pitchers-mound {
    opacity:1;
    fill:#b56700;
    fill-opacity:1;
    stroke:#85881b;
    stroke-width:2;
    stroke-linecap:round;
    stroke-linejoin:round;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }

  #right-baseline {
    fill:none;
    fill-opacity:0.75;
    fill-rule:evenodd;
    stroke:white;
    stroke-width:3.01047993;
    stroke-linecap:square;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }
  
  #left-baseline {
    fill:none;
    fill-opacity:0.75;
    fill-rule:evenodd;
    stroke:white;
    stroke-width:3;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }
  
  #third-base{
    opacity:1;
    fill:white;
    fill-opacity:1;
    stroke:none;
    stroke-width:3;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }
  
  #first-base {
    opacity:1;
    fill:white;
    fill-opacity:1;
    stroke:none;
    stroke-width:3;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }
  
  #second-base {
    opacity:1;
    fill:white;
    fill-opacity:1;
    stroke:none;
    stroke-width:3;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }
  
  #pitchers-mound-bump {
    opacity:1;
    fill:white;
    fill-opacity:1;
    stroke:none;
    stroke-width:3;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }
  
  #home-plate {
    fill:white;
    fill-opacity:1;
    stroke:none;
    stroke-width:3;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-opacity:1;
  }
  
  #right-batter-box {
    opacity:1;
    fill:#85881b;
    fill-opacity:1;
    stroke:white;
    stroke-width:1;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }
  
  #left-batter-box {
    opacity:1;
    fill:#85881b;
    fill-opacity:1;
    stroke:white;
    stroke-width:1;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }

  #catcher-box {
    opacity:1;
    fill:#85881b;
    fill-opacity:1;
    stroke:white;
    stroke-width:1;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }

  #third-coach-box {
    opacity:1;
    fill:#00a83b;
    fill-opacity:1;
    stroke:white;
    stroke-width:1.00000036;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }
  
  #first-coach-box {
    opacity:1;
    fill:#00a83b;
    fill-opacity:1;
    stroke:white;
    stroke-width:1.00000215;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }
  
  #left-on-deck {
    opacity:1;
    fill:#00a83b;
    fill-opacity:1;
    stroke:white;
    stroke-width:1;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }

  #right-on-deck {
    opacity:1;
    fill:#00a83b;
    fill-opacity:1;
    stroke:white;
    stroke-width:1;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }

  #home-dirt-border {
    opacity:1;
    fill:white;
    fill-opacity:1;
    stroke:none;
    stroke-width:3;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }

  #field {
    fill:#00a831;
    fill-opacity:1;
    fill-rule:evenodd;
    stroke:none;
    stroke-width:1px;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-opacity:1;
  }
  #batter-box-dirt {
    opacity:1;
    fill:#85881b;
    fill-opacity:1;
    stroke:none;
    stroke-width:1;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }

  #infield-dirt {
    opacity:1;
    fill:#a48e28;
    fill-opacity:1;
    stroke:#85881b;
    stroke-width:1.04379344;
    stroke-linecap:butt;
    stroke-linejoin:bevel;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }

  #hide-dirt-right {
    fill:#00a831;
    fill-opacity:1;
    fill-rule:evenodd;
    stroke:none;
    stroke-width:1px;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-opacity:1;
  }

  #hide-dirt-left {
    fill:#00a831;
    fill-opacity:1;
    fill-rule:evenodd;
    stroke:none;
    stroke-width:1px;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-opacity:1;
  }

  #hide-dirt-top {
    opacity:1;
    fill:#00a837;
    fill-opacity:1;
    stroke:#85881b;
    stroke-width:4.99999857;
    stroke-linecap:butt;
    stroke-linejoin:miter;
    stroke-miterlimit:4;
    stroke-dasharray:none;
    stroke-opacity:1;
  }

  .field-container {
    display: flex;
    justify-content: center;
    background-color: #00a831;

  }

  .background {
      width: 650px; /* Set the desired width for your SVG */
      height: 500px; /* Set the desired height for your SVG */
      width: 100%;
      height: 100vh;
      position: relative;
      outline: green solid 3px;
  }
  
  .foreground {
    width: 50%;
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
    max-width: 750px;
    /* adjust at will */
    color: black;
    padding: 1em;
    margin: 0 0 2em 0;
  }
    body {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
  }
  #output {
    font-family: monospace;
  }
</style>