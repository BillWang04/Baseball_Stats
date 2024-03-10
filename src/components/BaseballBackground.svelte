<script>
    import { fade, draw, fly } from 'svelte/transition';
    import { tweened } from "svelte/motion";
    import { cubicOut, cubicInOut } from "svelte/easing";

    export let index
    export let offset
    

    let backball = false;

    $: if (index >= 2) {
    backball = true;
    } else {
    backball = false;
    }




    // $: {
    //   b1X.set(327.5, { duration: 500})
    //   b1Y.set(205, {duration: 500})
    // }
    // $: {
    //   b2X.set(210, { duration: 500})
    //   b2Y.set(320, {duration: 500})
    // }





</script>
    
    {#if backball}

        <svg width="100%" height="100%" class = 'map' id="svg2" viewBox="0 0 650 500" 
        class:visible = {backball} in:fade={{ duration: 1000 }}
        out:fade = {{duration : 1000}}
         >

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
            {#if index === 3}
              <!-- first base -->
                <circle cx="445" cy="315" r="25" fill="yellow" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
                <text x="445" y="315" text-anchor="middle" dy=".3em" fill="black" font-size="16" font-weight="bold" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>1B</text>
              <!-- second base -->
              <circle cx="420" cy="215" r="25" fill="yellow" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
              <text x="420" y="215" text-anchor="middle" dy=".3em" fill="black" font-size="16" font-weight="bold" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>2B</text>
              <!-- third base -->
              <circle cx="215" cy="315" r="25" fill="yellow" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
                <text x="215" y="315" text-anchor="middle" dy=".3em" fill="black" font-size="16" font-weight="bold" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>3B</text>
              <!-- pitchers base -->
              <circle cx="330" cy="315" r="25" fill="yellow" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
                <text x="330" y="315" text-anchor="middle" dy=".3em" fill="black" font-size="16" font-weight="bold" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>P</text>
              <!-- short stop -->
              <circle cx="240" cy="215" r="25" fill="yellow" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
                <text x="240" y="215" text-anchor="middle" dy=".3em" fill="black" font-size="16" font-weight="bold" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>SS</text>
              <!-- center field -->
              <circle cx="330" cy="80" r="25" fill="orange" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
                <text x="330" y="80" text-anchor="middle" dy=".3em" fill="white" font-size="16" font-weight="bold" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>CF</text>
              <!-- left field -->
              <circle cx="140" cy="140" r="25" fill="orange" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
              <text x="140" y="140" text-anchor="middle" dy=".3em" fill="white" font-size="16" font-weight="bold" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>LF</text>
            <!-- right field -->
            <circle cx="520" cy="140" r="25" fill="orange" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
            <text x="520" y="140" text-anchor="middle" dy=".3em" fill="white" font-size="16" font-weight="bold" in:fly={{ y: -20, duration: 500 }} out:fly={{ y: -20, duration: 800 }}>RF</text>
             {/if}
            {#if index === 4 }
              <circle cx="327.5" cy="429" r="15" fill="blue"/>
            {/if}
            {#if index === 5}
            <circle id="homebase" cx="327.5" cy="429" r="15" fill="blue">
              <animate attributeName="cx" values="327.5;445;327.5" keyTimes="0;0.5;1" dur="4s" repeatCount="indefinite" />
              <animate attributeName="cy" values="429;320;205" keyTimes="0;0.5;1" dur="4s" repeatCount="indefinite" />
            </circle>

          <circle id="b2" cx="327.5" cy="205" r="15" fill="blue">
            <animate attributeName="cx" values="327.5;210;327.5" keyTimes="0;0.5;1" dur="4s" repeatCount="indefinite" />
            <animate attributeName="cy" values="205;320;429" keyTimes="0;0.5;1" dur="4s" repeatCount="indefinite" />
          </circle>

        {/if}

        {#if index === 6}
          {#if offset <= 0.1}
            <circle cx="327.5" cy="429" r="15" fill="blue" />
            <circle cx="275" cy="449" r="15" fill="blue"/>
            <circle cx="225" cy="469" r="15" fill="blue"/>
          {/if}

          {#if offset >= 0.1 && offset < .2}
            <circle cx="327.5" cy="429" r="15" fill="red" />
            <circle cx="275" cy="449" r="15" fill="blue"/>
            <circle cx="225" cy="469" r="15" fill="blue"/>
 
          {/if}

          {#if offset >= .2 && offset <.3}
            <circle cx="327.5" cy="429" r="15" fill="blue"  out:fly={{ y: -20, duration: 10 }}/>
            <circle cx="275" cy="449" r="15" fill="blue"/>
          {/if}

          {#if offset >= 0.3 && offset < .5}
            <circle cx="327.5" cy="429" r="15" fill="red"  out:fly={{ y: -20, duration: 10 }}/>
            <circle cx="275" cy="449" r="15" fill="blue"/>
          {/if}

          {#if offset >= 0.5 && offset < .6}
            <circle cx="327.5" cy="429" r="15" fill="blue" out:fly={{ y: -20, duration: 10 }}/> 
          {/if}

          {#if offset >=.6 && offset < .7}
            <circle cx="327.5" cy="429" r="15" fill="red" out:fly={{ y: -20, duration: 10 }}/>
          {/if}

          {#if offset >= .7}
            <circle cx="445" cy="315" r="15" fill="blue" in:fly={{ y: 600, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
            <!-- second base -->
            <circle cx="420" cy="215" r="15" fill="blue" in:fly={{ y: 600, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
            <!-- third base -->
            <circle cx="215" cy="315" r="15" fill="blue" in:fly={{ y: 600, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
            <!-- pitchers base -->
            <circle cx="330" cy="315" r="15" fill="blue" in:fly={{ y: 600, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
            <!-- short stop -->
            <circle cx="240" cy="215" r="15" fill="blue" in:fly={{ y: 600, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
            <!-- center field -->
            <circle cx="330" cy="80" r="15" fill="blue" in:fly={{ y: 600, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
            <!-- left field -->
            <circle cx="140" cy="140" r="15" fill="blue" in:fly={{ y: 600, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
          <!-- right field -->
          <circle cx="520" cy="140" r="15" fill="blue" in:fly={{ y: 600, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
          {/if}          

        {/if}

        {#if index === 7}
        <circle cx="327.5" cy="429" r="15" fill="blue" in:fly={{ y: 600, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
        {/if}

        {#if index === 8 || index === 9}
        <circle cx="328" cy="320" r="15" fill="blue" in:fly={{ y: 600, duration: 500 }} out:fly={{ y: -20, duration: 800 }}/>
        {/if}

            </g>
        </svg>
    {/if}



  <style>
    .map{
      opacity: 0;
      visibility: hidden;
    }
  
    .map.visible {
      opacity: 1;
      visibility: visible;
    }
  
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
  
    
  </style>