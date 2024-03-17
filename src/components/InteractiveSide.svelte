<script>
    import ScrollyTeller from "./ScrollyTeller.svelte";
    let percentage = "100%";
    let num_sections = 12;
    import { fade, draw, fly } from 'svelte/transition';
    import { tweened } from "svelte/motion";
    import { cubicOut, cubicInOut } from "svelte/easing";
    export let index;
    import Data from "./WarData.svelte"
    import PitchingData from "./pitchingData.svelte";
    import BattingData from "./battingData.svelte";


    function openNav() {
      document.getElementById("mySidenav").style.width = "400px";
      document.getElementById("foreground").style.marginLeft = "400px";
      document.getElementById("background").style.marginLeft = "400px";
      document.getElementById("background").style.width = "73%";
  
  
    }

    /* Set the width of the side navigation to 0 and the left margin of the page content to 0 */
    function closeNav() {
      document.getElementById("mySidenav").style.width = "0";
      document.getElementById("foreground").style.marginLeft = "auto";
      document.getElementById("background").style.marginLeft = "auto";
      document.getElementById("background").style.width = "100%";


  }

  $ : if (index >= 3 && index < num_sections - 1){
    openNav()
    }

  $ : if (index === 2 || index >= num_sections - 1){
      closeNav()
    }


    

</script>

    <div id="mySidenav" class="sidenav" >
        {#if index ===3 }
        <div class = "sidenav_text" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>
          <h2>Baseball Defensive Positions</h2>
          <ul>
            <li><strong>Pitcher (P):</strong> Throws the ball towards the batter.</li>
            <li><strong>Catcher (C):</strong> Receives the pitches and plays a crucial role in defense.</li>
            <li><strong>First Baseman (1B):</strong> Infielder positioned near first base.</li>
            <li><strong>Second Baseman (2B):</strong> Infielder positioned near second base.</li>
            <li><strong>Third Baseman (3B):</strong> Infielder positioned near third base.</li>
            <li><strong>Shortstop (SS):</strong> Infielder positioned between second and third base.</li>
            <li><strong>Left Fielder (LF):</strong> Outfielder positioned in left field.</li>
            <li><strong>Center Fielder (CF):</strong> Outfielder positioned in center field.</li>
            <li><strong>Right Fielder (RF):</strong> Outfielder positioned in right field.</li>
          </ul>
          <p>
            The outfielders are responsible for catching fly balls and preventing hits from reaching the edge of the field. 
            The infielders handle plays that involve tagging a base or runner and catch a batted ball before it leaves the infield. Each player has a specific role in fielding and preventing the offensive team from advancing around the bases.
          </p>

        </div>
        {/if}



        {#if index === 4}
        <div class = "sidenav_text" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>

        <h1>Batting</h1>
        <p>
          The team at bat sends one player at a time to the home plate to bat.
        </p>
        <p>
          The batter tries to hit the ball pitched by the opposing team's pitcher.
        </p>
        <p>
          If the batter hits the ball into fair territory and reaches at least first base safely, it's called a hit.
        </p>

        <h2>Fair Territory</h2>

        <p>
          1. You hit a fair ball that isn't caught by a fielder before it touches the ground.
      </p>
      
      <p>
          2. You hit a fair ball that touches the ground and is caught by a fielder whose throw fails to beat you to a base.
      </p>
      
      <p>
          3. The umpire calls four pitches out of the strike zone during your at-bat.
      </p>
      
      <p>
          4. A pitch in the strike zone hits you without first touching your bat.
      </p>
      
      <p>
          5. The catcher obstructs your swing.
      </p>
      
      <p>
          6. You hit a fair ball beyond the playing field (for a home run).
      </p>
      
      <p>
          7. You hit a fair, catchable ball, but the fielder drops the ball, throws it away, and so on.
      </p>
      
      <p>
          8. A third strike skips past the catcher and you beat the throw to first.
      </p>
      
        </div>
        
        
        {/if}
        {#if index === 5}
        <div class = "sidenav_text" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>
            <h2>Run:</h2>
            <p>
                A run is a point scored by a player or team in baseball. It is earned by a player who successfully crosses
                home plate after touching each of the bases (first, second, and third) in a counter-clockwise order. Players
                score runs by hitting the ball and reaching home plate before being tagged or by drawing walks and advancing
                around the bases.
            </p>
            <p>
                Runners on bases try to advance and score runs by running around the bases in a counterclockwise direction.
                A run is scored when a runner legally touches all four bases and returns safely to home plate.
            </p>
            
        </div>

        {/if}

        {#if index === 6}
        <div class = "sidenav_text">
            <h1>Outs and Innings in Baseball</h1>
            <p>In baseball, the concept of outs and innings is crucial to the game's structure and flow. Each team has three outs per inning to score as many runs as possible before switching between offense and defense.</p>

            <h2>Innings</h2>
            <p>An inning is divided into two halves: the top half and the bottom half. The visiting team bats in the top half of the inning, while the home team bats in the bottom half. During their respective half-innings, a team's objective is to score runs by advancing their batters around the bases while preventing the opposing team from recording three outs.</p>
            <p>A regulation baseball game typically consists of nine innings, with each team having the opportunity to bat and field in every inning. However, in the case of a tie after nine innings, additional innings (extra innings) are played until one team has scored more runs than the other at the end of a completed inning.</p>

            <h2>Outs</h2>
            <p>When a batter is out, they are removed from the bases, and the next batter in the lineup takes their turn at the plate. An out can be recorded in various ways:</p>
            <ul>
                <li><strong>Strikeouts:</strong> A strikeout occurs when the batter accumulates three strikes during their at-bat.</li>
                <li><strong>Foul Balls:</strong> If a batter hits a foul ball with two strikes already, they are out – this is known as a "foul tip" or a "foul out."</li>
                <li><strong>Fly Outs:</strong> When a batter hits a fly ball that is caught by a fielder before it hits the ground, it results in a fly out.</li>
                <li><strong>Ground Outs:</strong> If a batter hits a ground ball and a fielder throws to a base ahead of the runner, forcing them out, it is called a ground out or a force out.</li>
                <li><strong>Tag Outs:</strong> If a runner is off the base and a fielder tags them with the ball before they can return to the base, it is called a tag out.</li>
                <li><strong>Caught Stealing:</strong> When a runner attempts to steal a base, and the catcher throws to the base ahead of the runner, resulting in the runner being tagged out, it is called a "caught stealing" out.</li>
                <li><strong>Interference and Obstruction:</strong> In certain instances, outs can also be recorded due to interference by a runner or obstruction by a fielder, as determined by the umpires.</li>
            </ul>
        <p>a</p>
        <p>a</p>


                        
        </div>

        {/if}

        {#if index === 7}
          <h3>Distribuition of Batter Stats by Top Players from 2020 - 2023</h3>
          <BattingData/>
        {/if}

        {#if index === 8 }
        <div class = 'sidenav_text'>
            <h1>Pitching</h1>
            <p>
              <strong>SV (Sinker/Slider):</strong> A pitch that can behave as either a sinker or a slider. A sinker tends to move downward and may induce ground balls, while a slider has a lateral break.
            </p>
          
            <p>
              <strong>ST (Strike):</strong> A pitch thrown within the strike zone, aiming to be called a strike by the umpire.
            </p>
          
            <p>
              <strong>SL (Slider):</strong> A pitch with a lateral break, often sharper and smaller than a curveball. It can deceive batters with its movement.
            </p>
          
            <p>
              <strong>SI (Sinker):</strong> A pitch that tends to move downward, inducing ground balls. It has a sinking action, making it challenging for batters.
            </p>
          
            <p>
              <strong>KC (Knuckle Curve):</strong> A breaking ball with a noticeable curve or break. The "knuckle" in the name suggests a grip similar to a knuckleball, but with a curveball's spin.
            </p>
          
            <p>
              <strong>FS (Splitter):</strong> A pitch with downward movement, similar to a forkball or split-finger fastball. It can deceive batters with its change in speed and movement.
            </p>
          
            <p>
              <strong>FF (Four-seam Fastball):</strong> A high-speed pitch that typically travels in a straight line. The four seams on the ball provide less air resistance, allowing for maximum velocity.
            </p>
          
            <p>
              <strong>FC (Cutter):</strong> A fastball with lateral movement, often described as a "cutting" action. It can be challenging for batters to predict due to its late break.
            </p>
          
            <p>
              <strong>CU (Curveball):</strong> A slower pitch with a noticeable curve or break. It can be used to deceive batters with its change of trajectory.
            </p>
          
            <p>
              <strong>CH (Changeup):</strong> A slower pitch designed to deceive the batter with a change in speed. It mimics the arm action of a fastball but with reduced velocity.
            </p> 

            <p>The pitcher aims to throw pitches in the strike zone - the area over home plate between the batter's knees and mid-chest. If the batter doesn't swing at a pitch in the strike zone, it's called a strike. With three strikes, the batter is out</p>
            <p>a</p>
            <p>a</p>

        </div>
        
        {/if}

        {#if index === 9}
          <div>
            <h3>
              Distribution of Pitcher Stats Grouped by Pitch Type from 2020 - 2023
            </h3>
          </div>
          <PitchingData/>


        {/if}


        {#if index === 10}
        <!-- <div class ="sidenav_text" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}> -->
        <h1>Major League Baseball Wins Above Avg By Position</h1>
        <p></p>
          <!-- <a href="#">B2 (Base2)</a>
          <a href="#">B3 (Base3)</a>
          <a href="#">SS (Short Stop)</a>
          <a href="#">CF (Center Field)</a>
          <a href="#">LF (Left Field)</a>
          <a href="#">RF (Right Field)</a>
          <a href="#">P (Pitcher)</a> -->
          <Data {index}/>
          <p>
            Wins Above Average (WAA) in baseball is a metric used to evaluate a player's or a team's performance relative to the league average. It provides insight into how much a player or team has contributed to winning games compared to an average player or team in a given season. WAA is an advanced statistic that aims to go beyond traditional stats and provide a more comprehensive assessment of value.
          </p>
        <!-- </div> -->
        {/if}
        
      </div>



      

           


<style>

.sidenav {
    height: 100%;
    width: 0;
    position: fixed;
    z-index: 1;
    top: 0;
    background-color: lightgray;
    overflow-x: hidden;
    transition: 0.5s;
    padding-top: 30px;
    padding-bottom: 30px;
    left: 0;

    }




    @media screen and (max-height: 450px) {
    .sidenav {padding-top: 15px;}
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