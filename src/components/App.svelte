<script>
    import * as d3 from 'd3';
    import { onMount } from "svelte";

    let csv_war_data2023;
    let csv_war_data2022;
    let selectedColumn = "All_P"; 

    let update; // Declare the update function outside onMount
    let svg;
    let y;
    let x;
    let margin;
    let width;
    let height;

    async function fetchData(path) {
        let csv_data = await d3.csv(path);
        console.log(csv_data)
        return csv_data;
    }


    onMount(async () => {
        csv_war_data2023 = await fetchData('data2023/cleanedTWBP2023.csv');
        csv_war_data2022 = await fetchData('data2022/cleanedTWBP2022.csv');

        margin = { top: 30, right: 10, bottom: 70, left: 150 },
            width = 460 - margin.left - margin.right,
            height = 400 - margin.top - margin.bottom;

        // append the svg object to the body of the page
        svg = d3.select("#warBaseball")
            .append("svg")
            .attr("width", width + margin.left + margin.right)
            .attr("height", height + margin.top + margin.bottom)
            .append("g")
            .attr("transform","translate(" + margin.left + "," + margin.top + ")")


        svg.append("text").attr("x", width/2).attr("y", -10).attr("text-anchor", "middle")
        .style("font-size", "16px")
        .text("Wins Above Replacement for a Given Year");

  

        // X axis
        x = d3.scaleLinear()
            .range([0, width])
            .domain([-15, 15]);
        svg.append("g")
            .attr("transform", "translate(0," + height + ")")
            .call(d3.axisBottom(x));

        svg.append('text').attr("transform", "translate(" + (width/2) + " ," + (height+40) + ")")
        .style("text-anchor", "middle")
        .text("Wins Above Replacement (Pitching and Batting)");

        // Add Y axis
        y = d3.scaleBand()
            .domain(csv_war_data2023.map(function (d) { return d.Name; }))
            .range([0, height])
            .padding(0.2);
        svg.append("g")
            .attr("class", "myYaxis")
            .call(d3.axisLeft(y));

        svg.append("text")
            .attr("transform", "rotate(-90)")
            .attr("x", -(height/2))
            .attr("y", -120)
            .style("text-anchor", "middle")
            .text("Teams");

        // Initialize the plot with the first dataset
        update(csv_war_data2022);
    });

    // Define the update function outside onMount
    update = function (data) {
    var u = svg.selectAll("rect")
        .data(data);

    u.enter().append("rect")
        .merge(u)
        .transition()
        .duration(1000)
        .attr("y", function (d) { return y(d.Name); })
        .attr("x", function (d) { return x(-15); })
        .attr("height", y.bandwidth())
        .attr("width", function (d) { return width - x(d.All_P); })
        .attr("fill", "#69b3a2");
        
    }
</script>

<main>
    <!-- <label for="columns">Select a column:</label>
    <select bind:value={selectedColumn} id="columns">
        {#each Object.keys(csv_war_data2023[0]) as column}
            <option value={column}>{column}</option>
        {/each}
    </select> -->
    <button on:click={() => update(csv_war_data2022)}>2022</button>
    <button on:click={() => update(csv_war_data2023)}>2023</button>

    <!-- Create a div where the graph will take place -->
    <div id="warBaseball"></div>
</main>

 <style>

</style>
