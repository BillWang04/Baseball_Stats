<script>
    import App from "./WarData.svelte" 
    import * as d3 from 'd3';
    import 'd3-transition';
    import * as d3selection from 'd3-selection';
    import { onMount } from "svelte";
    import SubGraph from './SubGraph.svelte';

    let show = Array(9).fill("hidden");    
    let current_zoomed = false;

    let svg;
    let positions;
    let selectedPosition;

  const zoom = d3.zoom()
    .scaleExtent([1, 40])
    .on("zoom", zoomed).filter((event, selection) => {
    // Check if the event type is a mouse click event
    return event.type === "mousedown" && !event.touches; // Zoom only on mouse click
  });
  
  
  function zoomed(event) {
    const {transform} = event;
    d3.select(svg).attr("transform", transform);  
  }

function zoomIn(event, item) {
    event.preventDefault();
    event.stopPropagation();
    current_zoomed = true;
    let x = parseInt(item.attr("x"));
    let y = parseInt(item.attr("y"))
    const svgWidth = svg.getBoundingClientRect().width;
    const svgHeight = svg.getBoundingClientRect().height;

    const rectWidth = 100 * svgWidth/1040; // Width of the rectangle
    const rectHeight = 100 * svgHeight/800; // Height of the rectangle
    const centerX = x * svgWidth/1040 + (rectWidth / 2);
    const centerY = y * svgHeight/800 + rectHeight / 2;
    // console.log(x,y)

    // Calculate the translation needed to center the rectangle
    const translateX = svgWidth / 2 - (centerX * svgWidth/650)
    const translateY = svgHeight / 2 - (centerY * svgWidth/650)

    // console.log(svgWidth,svgHeight)
    d3.select(svg).transition()
        .duration(1500)
        .call(zoom.transform,
        d3.zoomIdentity.scale(5).translate(translateX,translateY)
    );

    }

    function reset() {
    show = Array(9).fill("hidden");
      d3.select(svg).transition().duration(1500).call(
        zoom.transform,
        d3.zoomIdentity,
        );
    current_zoomed = false;
    }

    $: {
      // d3.select(svg).call(zoom);
      positions = d3.select(svg).selectAll(".position");
      positions.on("click", (event) => {
        if (!current_zoomed && !d3.active(svg)) {
        selectedPosition = d3.select(svg).select(`#${event.target.id}`)
        show[Number(event.target.classList[1])] = 'visible';
        zoomIn(event,selectedPosition)
        selectedPosition.style('visibility', 'hidden');
        }});

    }

    $: d3.select(svg).on('click',(event) => {
      if (!d3.select(event.target).classed('position') && !d3.active(svg)) {
      reset()
      d3.select(svg).selectAll(".position").style('visibility', 'visible')}})
    $: d3.select(svg).on('wheel.zoom',null) 

</script>

<div class="field-container">
  <div class="margin">
  <button  onclick="location.href='../'">Return Home</button>
  </div>
    <svg bind:this={svg} width="1040" height= "800"id="svg2" viewBox="0 0 650 500">
  
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
        
        <g id='group-pos-first-base' width="100" height="100"  x="394" y="265" >
          <foreignObject id='group-pos-first-base-l' x="394" y="265" width="100" height="100" visibility={show[2]}>
            <SubGraph position="1B"/>
          </foreignObject>
          <rect class="position 2" id="pos-first-base" width="100" height="100"  x="394" y="265"/>
        </g>
        
        <g id='group-pos-second-base' width="100" height="100"  x="342" y="150" >
          <foreignObject id='group-pos-second-base-l' x="342" y="150" width="100" height="100" visibility={show[3]}>
            <SubGraph position="2B"/>
          </foreignObject>
          <rect class="position 3" id="pos-second-base" width="100" height="100"  x="342" y="150" />
        </g>
        
        <g id='group-pos-short-stop' width="100" height="100"  x="215" y="150" >
          <foreignObject id='group-pos-short-stop-l' x="215" y="150" width="100" height="100" visibility={show[5]}>
            <SubGraph position="SS"/>
          </foreignObject>
          <rect class="position 5" id="pos-short-stop" width="100" height="100"  x="215" y="150" />
        </g>

        <g id='group-pos-third-base' width="100" height="100"  x="164" y="265" >
          <foreignObject id='group-pos-third-base-l' x="164" y="265" width="100" height="100" visibility={show[4]}>
            <SubGraph position="3B"/>
          </foreignObject>
          <rect class="position 4" id="pos-third-base" width="100" height="100"  x="164" y="265" />
        </g>

        <g id='group-pos-pitcher' width="100" height="100"  x="277.5" y="265" >
          <foreignObject id='group-pos-pitcher-l' x="277.5" y="265" width="100" height="100" visibility={show[0]}>
            <SubGraph position="All_P"/>
          </foreignObject>
          <rect class="position 0" id="pos-pitcher" width="100" height="100"  x="277.5" y="265" />
        </g>

        <g id='group-pos-catcher' width="100" height="100"  x="277.5" y="380" >
          <foreignObject id='group-pos-catcher-l' x="277.5" y="380" width="100" height="100" visibility={show[1]}>
            <SubGraph position="C"/>
          </foreignObject>
          <rect class="position 1" id="pos-catcher" width="100" height="100"  x="277.5" y="380" />
        </g>

        <g id='group-pos-center-field' width="100" height="100"  x="277.5" y="10" >
          <foreignObject id='group-pos-center-field-l' x="277.5" y="10" width="100" height="100" visibility={show[7]}>
            <SubGraph position="CF"/>
          </foreignObject>
          <rect class="position 7" id="pos-center-field" width="100" height="100"  x="277.5" y="10" />
        </g>

        <g id='group-pos-right-field' width="100" height="100"  x="450" y="50" >
          <foreignObject id='group-pos-right-field-l' x="450" y="50" width="100" height="100" visibility={show[8]}>
            <SubGraph position="RF"/>
          </foreignObject>
          <rect class="position 8" id="pos-right-field" width="100" height="100"  x="450" y="50" />
        </g>

        <g id='group-pos-left-field' width="100" height="100"  x="100" y="50" >
          <foreignObject id='group-pos-left-field-l' x="100" y="50" width="100" height="100" visibility={show[6]}>
            <SubGraph position="LF"/>
          </foreignObject>
          <rect class="position 6" id="pos-left-field" width="100" height="100"  x="100" y="50" />
        </g>
  
  
  
      </g>
    </svg>
    <div class="margin">
    </div>
</div>



<style>
  
    .position {
      stroke:yellow;
      fill-opacity:0;
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
      /* height: 100em */
  
    }

    .margin {
      flex: 1
    }
</style>