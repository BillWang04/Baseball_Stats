<script>
  import ScrollyTeller from '../components/ScrollyTeller.svelte'
  import App from '../components/App.svelte'
  import BaseballField from '../components/BaseballField.svelte';
</script>


<ScrollyTeller/>
<App/>
<BaseballField/>

<main>
  <h2>Writeup</h2>
  <p>
    In our venture into the world of baseball analytics, we've undertaken the challenge of not just visualizing the game's overall stats but immersing our audience in the intricate gameplay dynamics. The centerpiece of our project is a captivating scrollable element, carefully crafted to unveil the nuanced layers of baseball, from gameplay strategies to compelling statistical insights. We have created a scrollable element that should describe how the game is played and significant plots that we found in the data. Moreover, we have a clickable svg where if you click on a box, it will zoom in onto that box and we want to add stats and to be able to drill down on the plots. We have shown a plot when you click on a certain box after it zooms. We have had a considerable amount of difficulty actually acquiring, compiling and cleaning data and another challenge is probably adding data for each position of the svg. The data is very sparse and spread out and every resource we encountered seemed to carry its unique flaws, adding a layer of complexity to our mission. Additionally, for the interactions, there will be lots of dependencies to consider as clicking on a section should trigger filtration of plots for different positions and perhaps players.
  </p>
</main>
<style>



</style>