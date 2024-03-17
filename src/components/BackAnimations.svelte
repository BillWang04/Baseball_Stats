<script>
    import { fade, draw, fly } from 'svelte/transition';
    import { tweened } from "svelte/motion";
    import { cubicOut, cubicInOut } from "svelte/easing";
    import BattingData, {battingWriteable} from "./battingData.svelte";
    import { pitchingWritable } from './pitchingData.svelte';
    $: console.log('pitching: ' + $pitchingWritable)
    $: console.log('index: ' + index)
    export let index;

    // const




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
    
   

    <div class ='field_explanation' in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>
      <p>
        The baseball field is divided into the infield and the outfield. The infield is a square area around the home plate, where most of the action takes place. The outfield is the grassy area beyond the infield, where the outfielders position themselves.
    </p>

    
    <p>
        The game is typically played over nine innings, with each team having a turn to bat and a turn to field in each inning. The team with the most runs at the end of the nine innings is declared the winner.
    </p>
    
    </div>
    
    {/if}


    {#if index === 7}
        {#if $battingWriteable === "pa"}
        <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
                <p>Plate Appearance Percentage is not a standard baseball statistic or metric. It's possible you might be referring to Plate Appearance (PA) or perhaps another metric or concept related to plate appearances.</p>
                <p>Plate Appearance (PA) refers to the total number of times a batter has come to the plate in a game. This includes appearances that result in various outcomes such as hits, walks, strikeouts, sacrifices, and hit-by-pitches. It's a fundamental statistic used to evaluate a batter's performance and is often used as a denominator in calculating other statistics like batting average, on-base percentage, and slugging percentage.</p>
                <p>If you're referring to another specific metric or concept related to plate appearances, please provide more context or clarification so I can better assist you.</p>

        </div>
        {/if}
    {#if $battingWriteable === "k_percent"}
    <div class = 'text_descript'in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}> 
        <p>Strikeout Percentage, often abbreviated as K%, is a baseball statistic that represents the percentage of plate appearances that result in a strikeout for a batter. It is calculated by dividing the number of strikeouts by the total number of plate appearances and multiplying by 100.</p>
        <p>Strikeout Percentage is used to evaluate a batter's ability to make contact with the ball. A lower strikeout percentage indicates better bat-to-ball skills, while a higher percentage suggests a tendency to strike out frequently.</p>
        <p>While strikeouts are often considered detrimental to a hitter's performance since they result in an automatic out, some power hitters may have higher strikeout percentages due to their aggressive approach at the plate, prioritizing power over contact.</p>
        <p>Comparing a player's strikeout percentage to league averages or historical benchmarks can provide insights into their hitting approach and overall effectiveness as a batter.</p>
        </div>
    {/if}
    {#if $battingWriteable === "bb_percent"}
    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
        <p>Walk Percentage, often abbreviated as BB%, is a baseball statistic that represents the percentage of plate appearances that result in a walk for a batter. It is calculated by dividing the number of walks by the total number of plate appearances and multiplying by 100.</p>
        <p>Walk Percentage is used to evaluate a batter's ability to exercise patience and select pitches effectively. Batters with high walk percentages demonstrate a keen eye for the strike zone and are adept at drawing walks, which can contribute to extending innings and putting pressure on opposing pitchers.</p>
        <p>Walk Percentage is often considered a positive attribute for hitters, as it reflects their ability to reach base without putting the ball in play, thereby increasing their on-base percentage and providing opportunities for their teammates to drive them in.</p>
        <p>Comparing a player's walk percentage to league averages or historical benchmarks can help assess their plate discipline and overall offensive value as a batter.</p>

        </div>
    {/if}
    {#if $battingWriteable === "woba"}
    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
            <p>wOBA stands for Weighted On-Base Average, which is a sabermetric baseball statistic used to measure a hitter's overall offensive value. It's considered one of the more comprehensive offensive metrics because it takes into account a hitter's ability to get on base and hit for power, while also adjusting for the value of different types of hits.</p>
            <p>The formula for calculating wOBA assigns specific weights to each offensive event based on its actual run value. These weights are derived from historical data to reflect the average number of runs a team can expect to score given each type of offensive outcome (single, double, triple, home run, walk, hit by pitch). Then, the formula calculates the sum of these weighted outcomes and divides it by the total number of plate appearances.</p>
            <p>In simpler terms, wOBA gives a more accurate picture of a hitter's offensive contribution than traditional statistics like batting average or on-base percentage because it considers the varying values of different offensive outcomes and weights them accordingly.</p>
            <p>A league-average wOBA is typically around .320-.330, with elite hitters often posting wOBA values above .400. Comparing a player's wOBA to the league average or historical benchmarks can help assess their offensive prowess relative to their peers.</p>
        </div>
    {/if}

    {#if $battingWriteable === "xwoba"}
    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
        <p>xwOBA, or expected Weighted On-Base Average, is a more advanced metric derived from Statcast data in baseball. It uses launch angle, exit velocity, and, in some cases, sprint speed to calculate the expected outcome of each batted ball based on similar historical batted balls.</p>
        <p>The concept of xwOBA is similar to regular wOBA, but instead of using the actual outcomes of batted balls, it calculates the expected outcomes based on the quality of contact. For example, a ball hit with a high exit velocity and favorable launch angle would have a higher expected wOBA than a weakly hit ball.</p>
        <p>xwOBA is useful for evaluating a hitter's underlying skills, independent of factors like defense or luck. It provides insight into whether a player's hitting performance is sustainable based on the quality of contact they're making.</p>

    </div>
    {/if}
    {#if $battingWriteable === "sweet_spot_percent"}
    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
        <p>Sweet Spot Percentage refers to the percentage of times a batter makes contact with the ball in what is considered the "sweet spot" of the bat. The sweet spot is the area on the bat where maximum energy transfer occurs upon contact with the ball, resulting in optimal batted ball outcomes.</p>
        <p>While there isn't a standardized metric for sweet spot percentage in baseball statistics, it can be inferred from metrics like exit velocity and launch angle, which are often used to assess the quality of contact a batter makes. Batters who consistently make contact in the sweet spot are more likely to generate hard-hit balls with favorable trajectories, leading to better offensive performance.</p>
        <p>Understanding a player's sweet spot percentage can provide insights into their ability to make solid contact and drive the ball effectively. However, it's important to note that the concept of sweet spot percentage may vary depending on individual hitting mechanics and preferences.</p>

        </div>
    {/if}
    {#if $battingWriteable === "barrel_batted_rate"}
    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
        <p>The Barrel Batted Rate is calculated by dividing the number of barrels hit by a batter by their total number of batted ball events and expressing it as a percentage.</p>
        <p>This metric is particularly useful for evaluating a hitter's ability to consistently make high-quality contact. Hitters with a high Barrel Batted Rate often demonstrate strong bat speed, good plate discipline, and the ability to drive the ball effectively.</p>
        <p>Barrel Batted Rate is a valuable tool for assessing a player's offensive performance beyond traditional statistics like batting average or home runs. It provides insights into the quality of contact a hitter makes, which can be predictive of future success.</p>
        <p>Comparing a player's Barrel Batted Rate to league averages or historical benchmarks can help identify standout performers and potential breakout candidates.</p>

    </div>
    {/if}
    {#if $battingWriteable === "hard_hit_percent"}
    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
        <p>Hard Hit Percentage is a baseball statistic that measures the percentage of a player's batted balls that are classified as "hard-hit" based on their exit velocity off the bat.</p>
        <p>This metric is typically calculated by dividing the number of hard-hit balls by the total number of batted balls and expressing it as a percentage.</p>
        <p>Hard-hit balls are generally defined as those with an exit velocity above a certain threshold, often set at 95 miles per hour or higher. These batted balls tend to result in more favorable offensive outcomes, such as extra-base hits or higher batting averages.</p>
        <p>Hard Hit Percentage provides valuable insights into a player's ability to make solid contact with the ball, which can be indicative of their offensive performance. Hitters with a high Hard Hit Percentage often demonstrate good bat speed, strength, and the ability to drive the ball with authority.</p>
        <p>Comparing a player's Hard Hit Percentage to league averages or historical benchmarks can help evaluate their ability to consistently make quality contact and contribute offensively.</p>

        </div>
    {/if}
    {#if $battingWriteable === "avg_best_speed"}
    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
        <p>Average Speed is a metric in baseball that measures a player's speed on the basepaths or in the field. It represents the average velocity at which a player moves over a certain distance, typically expressed in miles per hour (mph) or feet per second (fps).</p>
        <p>This metric is often used to evaluate a player's overall athleticism and ability to impact the game with speed. Players with above-average speed can be more effective at stealing bases, stretching hits into extra bases, and covering ground defensively.</p>
        <p>Average Speed can be measured using various technologies, including radar guns, GPS trackers, or player tracking systems like Statcast in Major League Baseball.</p>
        <p>Coaches and scouts use Average Speed as a tool for player evaluation and roster decisions, particularly in assessing players' abilities to excel in specific roles such as leadoff hitters or defensive specialists.</p>
        <p>Comparing a player's Average Speed to league averages or historical benchmarks can provide insights into their speed relative to their peers and their potential impact on the game.</p>

    </div>
    {/if}  
    {#if $battingWriteable === "avg_hyper_speed"}

    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
        <p>Average Hyper Speed is a hypothetical metric in baseball that could potentially measure a player's speed on the basepaths or in the field, with a focus on extremely fast bursts of movement.</p>
        <p>This metric would represent the average velocity at which a player executes high-speed movements over short distances, typically expressed in miles per hour (mph) or feet per second (fps).</p>
        <p>Average Hyper Speed could be particularly relevant for evaluating a player's ability to steal bases, chase down fly balls or line drives in the outfield, or make quick defensive plays in the infield.</p>
        <p>While Average Hyper Speed is not currently a standardized metric in baseball, advancements in player tracking technology, such as Statcast, could potentially allow for the measurement and analysis of such high-speed movements in the future.</p>
        <p>Coaches, scouts, and analysts might use Average Hyper Speed as a tool for assessing a player's explosiveness and agility, which can be valuable assets in various aspects of the game.</p>

    </div>
    {/if}  
    {#if $battingWriteable === "whiff_percent"}
    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
        <p>Whiff Percentage, often abbreviated as Whiff%, is a baseball statistic that measures the percentage of swings a batter misses on pitches thrown to them.</p>
        <p>It is calculated by dividing the total number of swings and misses by the total number of swings and expressing it as a percentage.</p>
        <p>Whiff Percentage is used to evaluate a batter's ability to make contact with the ball. A lower whiff percentage indicates better bat-to-ball skills, while a higher percentage suggests a tendency to swing and miss frequently.</p>
        <p>High whiff percentages can indicate weaknesses in a batter's plate discipline, pitch recognition, or timing. Batters with consistently high whiff percentages may struggle to put the ball in play effectively, leading to lower offensive production.</p>
        <p>Whiff Percentage is often considered alongside other metrics like contact rate and strikeout percentage to provide a comprehensive assessment of a batter's approach at the plate.</p>
        <p>Comparing a player's whiff percentage to league averages or historical benchmarks can help identify areas for improvement and evaluate their overall offensive performance.</p>
    </div>
    {/if}  
    {#if $battingWriteable === "swing_percent"}
    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
        <p>Swing Percentage, also known as Swing Rate, is a baseball statistic that measures the percentage of pitches a batter swings at, out of the total number of pitches thrown to them.</p>
        <p>It is calculated by dividing the number of swings by the total number of pitches (swings + called strikes + balls) and expressing it as a percentage.</p>
        <p>Swing Percentage is used to evaluate a batter's aggressiveness at the plate. A higher swing percentage indicates a more aggressive approach, while a lower percentage suggests a more selective approach, waiting for pitches in the strike zone.</p>
        <p>High swing percentages can indicate that a batter is willing to expand the strike zone and chase pitches outside of it, potentially leading to more swings and misses and lower on-base percentages.</p>
        <p>Swing Percentage is often considered alongside other metrics like contact rate, whiff percentage, and walk rate to provide a comprehensive assessment of a batter's plate discipline and approach.</p>
        <p>Comparing a player's swing percentage to league averages or historical benchmarks can help evaluate their plate discipline and overall offensive performance.</p>

    </div>
    {/if}  
    {/if}


    {#if index === 9 }
    {#if $pitchingWritable === "n_pitches"}
    <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
        <p>Number of Pitches is a baseball statistic that measures the total number of pitches thrown to a batter by a pitcher during their plate appearance.</p>
        <p>This statistic includes all pitches thrown, whether they are swung at by the batter, called strikes, balls, or pitches that are fouled off. It provides insights into the length and depth of a batter's plate appearance and the workload placed on the pitcher.</p>
        <p>Number of Pitches can be influenced by various factors, including the batter's plate discipline, the pitcher's strategy, the count, and the game situation. Longer plate appearances with a higher number of pitches can be indicative of a batter's ability to work deep into counts, tire out the pitcher, and potentially draw walks or make solid contact.</p>
        <p>For pitchers, a high number of pitches thrown per plate appearance can increase fatigue and impact their effectiveness over the course of a game or season.</p>
        <p>Coaches, analysts, and scouts use Number of Pitches to assess a batter's plate discipline, a pitcher's efficiency, and the overall competitiveness of a plate appearance.</p>
    
    </div>
   {/if}
   {#if $pitchingWritable === "release_speed"}
   <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}> 
    <p>Release Speed in pitching refers to the velocity at which a pitcher releases the ball during their pitching motion.</p>
    <p>This metric is typically measured in miles per hour (mph) and provides valuable information about the pitcher's fastball velocity or the speed of their off-speed pitches such as curveballs, sliders, or changeups.</p>
    <p>Release Speed is a crucial aspect of a pitcher's arsenal as it directly impacts the effectiveness of their pitches. A faster release speed generally translates to a faster pitch, making it more challenging for batters to react and make solid contact.</p>
    <p>Pitchers with higher release speeds on their fastballs can generate more strikeouts, induce weak contact, and maintain better control over the game.</p>
    <p>Release Speed is closely monitored by coaches, scouts, and analysts to assess a pitcher's velocity, pitch repertoire, and potential for success on the mound. It also serves as a key component in player development and refining pitching mechanics.</p>
    <p>Comparing a pitcher's release speed to league averages or historical benchmarks can provide insights into their performance, potential, and ability to compete at various levels of play.</p>
    </div>
   {/if}
   {#if $pitchingWritable === "spin_rate"}
   <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
    <p>Spin Rate in pitching refers to the rate at which a baseball spins when thrown by a pitcher, measured in revolutions per minute (RPM).</p>
    <p>This metric provides insights into the movement and effectiveness of a pitcher's pitches. Higher spin rates generally result in more movement and deception, making pitches harder for batters to track and hit.</p>
    <p>Spin Rate is particularly important for breaking balls such as curveballs and sliders, as well as for off-speed pitches like changeups. For fastballs, spin rate can influence the pitch's perceived velocity and movement, affecting its effectiveness.</p>
    <p>Pitchers with higher spin rates on breaking balls can generate sharper, more pronounced movement, making these pitches more challenging for batters to make solid contact with.</p>
    <p>Spin Rate is a crucial component in pitching analysis, player development, and scouting. Coaches and analysts use spin rate data to evaluate pitch quality, identify effective pitches, and optimize pitch selection and sequencing.</p>
    <p>Comparing a pitcher's spin rates to league averages or historical benchmarks can provide insights into their effectiveness, potential, and ability to succeed at various levels of play.</p>

    </div>
   {/if}
   {#if $pitchingWritable === "movement_inches"}
   <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
    <p>Movement Inches in pitching refers to the distance in inches that a pitch deviates from its expected trajectory as it approaches home plate.</p>
    <p>This metric provides insights into the movement and deception of a pitcher's pitches. It measures the horizontal and vertical displacement of the pitch relative to its initial release point and expected path.</p>
    <p>Positive movement inches indicate movement away from the pitcher's arm side, while negative movement inches indicate movement toward the arm side.</p>
    <p>Movement Inches are crucial for evaluating pitch quality and effectiveness. Pitches with greater movement inches can be more challenging for batters to track and hit, leading to swings and misses, weak contact, or called strikes.</p>
    <p>Pitchers often aim to maximize movement inches on their pitches to enhance their effectiveness and keep batters off balance. However, excessive movement can sometimes lead to control issues or difficulty commanding the strike zone.</p>
    <p>Coaches, analysts, and scouts use movement inches data to assess pitch movement, identify effective pitches, and provide feedback to pitchers for improvement.</p>
    <p>Comparing a pitcher's movement inches to league averages or historical benchmarks can provide insights into their pitch repertoire, effectiveness, and potential for success.</p>
    </div>
   {/if}

   {#if $pitchingWritable === "active_spin"}
   <div class = 'text_descript' in:fade|global={{ duration: 800 }} out:fly={{ y: -20, duration: 800 }}>
    <p>Active Spin Percentage is a baseball metric that measures the percentage of a pitch's spin that contributes to its movement, independent of its velocity.</p>
    <p>This metric is particularly relevant for analyzing breaking balls such as curveballs and sliders, where the spin of the ball influences its trajectory and movement as it approaches home plate.</p>
    <p>Active Spin Percentage helps assess the quality and effectiveness of a pitcher's breaking pitches. A higher active spin percentage indicates that a greater portion of the spin is contributing to the pitch's movement, making it more deceptive and challenging for hitters to track and hit.</p>
    <p>Coaches, scouts, and analysts use Active Spin Percentage to evaluate pitch quality, identify effective pitches, and provide feedback to pitchers for improvement.</p>
    <p>Comparing a pitcher's Active Spin Percentage to league averages or historical benchmarks can provide insights into their pitch repertoire, effectiveness, and potential for success.</p>

   </div>
  {/if}

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
  .text_descript {
      position: absolute;
      background: rgba(170, 51, 120, 0.2); /* 40% opaque */
      visibility: visible;
      position: fixed;
      margin-top: 15%;
      margin-left: 10%;
      z-index: 1; /* Ensure the div appears on top of other elements */
      width: 50%; /* Adjust this value to your desired width */
      padding: 10px; /* Add some padding for spacing between the content and the div's edges */
      box-sizing: border-box; 
      font-size: 24;
  }
  

</style>