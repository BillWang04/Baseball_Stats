<script>
  import ScrollyTeller from '../components/ScrollyTeller.svelte'
  import BaseballField from '../components/BaseballField.svelte';
  // import SideBar from '../components/InteractiveSide.svelte'
</script>
<head>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Permanent+Marker&display=swap" rel="stylesheet">
</head>

<!-- <SideBar/> -->
<ScrollyTeller/>

<main>
  <h2>Writeup</h2>
  <p>
    For our data analysis on baseball, we've tried to not only visualize the game's overall stats but immersing the audience in the intricate gameplay dynamics. The centerpiece of our project is a captivating scrollable element, carefully crafted to unveil the nuanced layers of baseball, from gameplay strategies to compelling statistical insights. We have created a scrollable element that should describe how the game is played and a significant plot that we found in the data. Moreover, we have a clickable svg where if you click on a box, it will zoom in onto that box and we want to add stats and to be able to drill down on the plots. We have shown a plot when you click on a certain box after it zooms. We also have a little simulation that we want to use as a way to show how baseball works. We would like to add animations to the simulation but that is for another day. We have had a considerable amount of difficulty actually acquiring, compiling and cleaning data and another challenge is probably adding data for each position of the svg. The data is very sparse and spread out and every resource we encountered seemed to carry its unique flaws, adding a layer of complexity to our mission. Additionally, for the interactions, there will be lots of dependencies to consider as clicking on a section should trigger filtration of plots for different positions and perhaps players. The clicking of the svg is also nifty and very buggy. It seems there are a lot of kinks that need to be worked out especially when it comes to the interaction between the svg and the scrollable element. 
  </p>
</main>


<button id="" onclick="location.href='/test'">Explore For Yourself!</button>