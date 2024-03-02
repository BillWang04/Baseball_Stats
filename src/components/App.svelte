<script>
  import * as d3 from 'd3';
  import { onMount } from "svelte";

  let csv_war_data2023;
  let csv_war_data2022;

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

      margin = { top: 30, right: 10, bottom: 70, left: 120 },
          width = 460 - margin.left - margin.right,
          height = 400 - margin.top - margin.bottom;

      // append the svg object to the body of the page
      svg = d3.select("#my_dataviz")
          .append("svg")
          .attr("width", width + margin.left + margin.right)
          .attr("height", height + margin.top + margin.bottom)
          .append("g")
          .attr("transform",
              "translate(" + margin.left + "," + margin.top + ")");

      // X axis
      x = d3.scaleLinear()
          .range([0, width])
          .domain([-15, 15]);
      svg.append("g")
          .attr("transform", "translate(0," + height + ")")
          .call(d3.axisBottom(x));

      // Add Y axis
      y = d3.scaleBand()
          .domain(csv_war_data2023.map(function (d) { return d.Name; }))
          .range([0, height])
          .padding(0.2);
      svg.append("g")
          .attr("class", "myYaxis")
          .call(d3.axisLeft(y));

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
  <button on:click={() => update(csv_war_data2023)}>2023</button>
  <button on:click={() => update(csv_war_data2022)}>2022</button>

  <!-- Create a div where the graph will take place -->
  <div id="my_dataviz"></div>
</main>

<style>

</style>
