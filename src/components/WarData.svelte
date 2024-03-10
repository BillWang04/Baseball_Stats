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
        // console.log(csv_data)
        return csv_data;
    }

    // $: update(csv_war_data2022, selectedColumn)


    onMount(async () => {
        csv_war_data2023 = await fetchData('data2023/cleanedTWBP2023.csv');
        csv_war_data2022 = await fetchData('data2022/cleanedTWBP2022.csv');
        

        margin = { top: 30, right: 10, bottom: 70, left: 150 },
            width = 400 - margin.left - margin.right,
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
        .text("Wins Above Avg by Position");

        // X axis
        x = d3.scaleLinear()
            .range([0, width])
            .domain([-15, 15]);
        svg.append("g")
            .attr("transform", "translate(0," + height + ")")
            .call(d3.axisBottom(x));

        svg.append('text').attr("transform", "translate(" + (width/2) + " ," + (height+40) + ")")
        .style("text-anchor", "middle")
        .text("Wins Above Avg By Position");
        

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
        update(csv_war_data2023, selectedColumn);
    });

    // Define the update function outside onMount
    update = function (data, selectedColumn) {
    var u = svg.selectAll("rect")
        .data(data);

    u.enter().append("rect")
        .merge(u)
        .transition()
        .duration(1000)
        .attr("y", function (d) { return y(d.Name); })
        .attr("x", function (d) { return x(-15); })
        .attr("height", y.bandwidth())
        .attr("width", function (d) { return width - x(d[selectedColumn]); }) // Use d[selectedColumn] instead of d.All_P
        .attr("fill", "#12365c");
    }
</script>

<main>

    <!-- Create a div where the graph will take place -->
    <div id="warBaseball" ></div>

    <button on:click={() => update(csv_war_data2022, selectedColumn)}>2022</button>
    <button on:click={() => update(csv_war_data2023, selectedColumn)}>2023</button>
    
    <div>
        <label for="column-select">Select Column and Click Year:</label>
        <select id="column-select" bind:value={selectedColumn}>
            <option value="All_P">All_P</option>
            <option value="SP">SP</option>
            <option value="RP">RP</option>
            <option value="Non-P">Non-P</option>
            <option value="C">C</option>
            <option value="1B">1B</option>
            <option value="2B">2B</option>
            <option value="3B">3B</option>
            <option value="SS">SS</option>
            <option value="LF">LF</option>
            <option value="CF">CF</option>
            <option value="RF">RF</option>
            <option value="OF (All)">OF (All)</option>
            <option value="DH">DH</option>
            <option value="PH">PH</option>
        </select>

    </div>

</main>

 <style>



</style>
