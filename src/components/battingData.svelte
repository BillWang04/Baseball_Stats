<script  context="module">
    import {writable} from 'svelte/store';
    export let battingWriteable =  writable('woba'); 

</script>
<script>
    import * as d3 from 'd3';
    import { onMount } from "svelte";
    import { afterUpdate } from "svelte";

    let csv_batting_data;
    let selectedColumn = "woba";

    let updateHistogram;
    let svg;
    let y;
    let x;
    let margin;
    let width;
    let height;

    async function fetchData(path) {
        let csv_data = await d3.csv(path);
        return csv_data;
    }

    onMount(async () => {
        csv_batting_data = await fetchData('stats.csv');
        margin = { top: 10, right: 30, bottom: 30, left: 40 };
        width = 420 - margin.left - margin.right;
        height = 400 - margin.top - margin.bottom;

        // Append the SVG object to the body of the page
        svg = d3.select("#my_dataviz")
            .append("svg")
            .attr("width", width + margin.left + margin.right)
            .attr("height", height + margin.top + margin.bottom)
            .append("g")
            .attr("transform", "translate(" + margin.left + "," + margin.top + ")");

        // Initialize the scales and axis
        x = d3.scaleLinear()
            .range([0, width]);

        y = d3.scaleLinear()
            .range([height, 0]);

        svg.append("g")
            .attr("class", "x-axis")
            .attr("transform", "translate(0," + height + ")");

        svg.append("g")
            .attr("class", "y-axis");

        svg.select(".y-axis-label")
            .text("Frequency")  // Change this to your desired label
            .attr("transform", "rotate(-90)")
            .attr("text-anchor", "middle")
            .attr("dy", "-4em");

        // Initial rendering of the histogram
        updateHistogram(selectedColumn);
    });

    updateHistogram = function (selectedColumn, firstTime) {
        // Find the minimum and maximum values of the selected column
        const extentValues = d3.extent(csv_batting_data, d => {
        // Convert the string to a float, if it's a string
        return typeof d[selectedColumn] === 'string' ? parseFloat(d[selectedColumn]) : d[selectedColumn];
    });              
        const minValue = extentValues[0];
        const maxValue = extentValues[1];

        // Update the x scale domain
        x.domain([minValue, maxValue]);

        // Update the histogram bins
        var histogram = d3.histogram()
            .value(function (d) { return d[selectedColumn]; })
            .domain(x.domain())
            .thresholds(x.ticks(10));

        var bins = histogram(csv_batting_data);

        // Update the y scale domain
        y.domain([0, d3.max(bins, function (d) { return d.length; })]);

        // Update the x and y axes
        svg.select(".x-axis")
            .transition()
            .call(d3.axisBottom(x));

        svg.select(".y-axis")
            .transition()
            .call(d3.axisLeft(y));

            
            d3.select("#my_dataviz").select("div").remove()

            var tooltip = d3.select("#my_dataviz")
                .append("div")
                .style("opacity", 0)
                .attr("class", "tooltip")
                .style("background-color", "black")
                .style("color", "white")
                .style("border-radius", "5px")
                .style("padding", "10px")

        // A function that change this tooltip when the user hover a point.
        // Its opacity is set to 1: we can now see it. Plus it set the text and position of tooltip depending on the datapoint (d)
        var showTooltip = function(event,d) {
            tooltip
                .transition()
                .duration(100)
                .style("opacity", 1);
            tooltip
                .html("Frequency: " + d.length)
                .style("left", (d3.pointer(event)[0] + 20) + "px")
                .style("top", (d3.pointer(event)[1]) + "px");
        }

        var moveTooltip = function(event,d) {
            tooltip
                .style("left", (d3.pointer(event)[0] + 20) + "px")
                .style("top", (d3.pointer(event)[1]) + "px");
        }
        // A function that change this tooltip when the leaves a point: just need to set opacity to 0 again
        var hideTooltip = function(d) {
            tooltip
            .transition()
            .duration(100)
            .style("opacity", 0)
        }

        // Update the histogram bars
        var bars = svg.selectAll("rect")
            .data(bins);

        bars.enter()
            .append("rect")
            .merge(bars)
            .attr("x", 1)
            .attr("transform", function (d) { return "translate(" + x(d.x0) + "," + y(d.length) + ")"; })
            .attr("width", function (d) { return x(d.x1) - x(d.x0) - 1; })
            .attr("height", function (d) { return height - y(d.length); })
            .style("fill", "#12365c")
            .on("mouseover", showTooltip )
            .on("mousemove", moveTooltip )
            .on("mouseleave", hideTooltip );

        bars.exit().remove();
    }
    $: battingWriteable.set(selectedColumn);
</script>

<main>
    <div id="my_dataviz"></div>

    <label for="column-select">Select Column:</label>
<select id="column-select" bind:value={selectedColumn}>
  <option value="pa">Plate Appearances (PA)</option>
  <option value="k_percent">Strikeout Percentage (K%)</option>
  <option value="bb_percent">Walk Percentage (BB%)</option>
  <option value="woba">Weighted On-Base Average (wOBA)</option>
  <option value="xwoba">Expected Weighted On-Base Average (xwOBA)</option>
  <option value="sweet_spot_percent">Sweet Spot Percentage</option>
  <option value="barrel_batted_rate">Barrel Batted Rate</option>
  <option value="hard_hit_percent">Hard Hit Percentage</option>
  <option value="avg_best_speed">Average Best Speed</option>
  <option value="avg_hyper_speed">Average Hyper Speed</option>
  <option value="whiff_percent">Whiff Percentage</option>
  <option value="swing_percent">Swing Percentage</option>
  <!-- Add more options for other columns -->
</select>

    <button on:click={() => updateHistogram(selectedColumn)}>Click to Update</button>
   
   

</main>

<style>



</style>