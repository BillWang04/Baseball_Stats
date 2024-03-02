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
    The purpose of our project is to visualize and discuss Baseball’s overall stats, gameplay and what a good player is. We have created a scrollable element that should describe how the game is played and significant plots that we found in the data. Moreover, we have a clickable svg where if you click on a box, it will zoom in onto that box and we want to add stats and to be able to drill down on the plots. We have shown a plot that may show how each zoom may look but it is far from complete. We have had a considerable amount of difficulty  actually acquiring, compiling and cleaning data and another challenge  is probably adding data for each position of the svg. The data is very sparse and spread out and every resource has major flaws in how it collects the data. Moreover, for the interactions, there will be lots of dependencies to consider as clicking on a section should trigger filtration of plots for different positions and perhaps players.
  </p>
</main>
<style>



</style>