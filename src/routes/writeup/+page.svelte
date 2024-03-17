<div id="writeup-container">

  <div class="button-container">
    <div class="buttons" onclick="location.href='../'">Return Home</div >
    <div class="buttons" onclick="location.href='https://youtu.be/1SelsiPbrm8'">Video</div>
    <div class="buttons" onclick="location.href='./test'">Explore WAA</div>
  </div>

  <h2>Writeup</h2>
  <p>
    For our data analysis on baseball, we've tried to not only visualize the game's overall stats but immersing the audience in the intricate gameplay dynamics. The centerpiece of our project is a captivating scrollable element, carefully crafted to unveil the nuanced layers of baseball, from gameplay strategies to compelling statistical insights. We have created a scrollable element that should describe how the game is played and a significant plot that we found in the data. Moreover, we have a clickable svg where if you click on a box, it will zoom in onto that box and we want to add stats and to be able to drill down on the plots. We have shown a plot when you click on a certain box after it zooms. We also have a little simulation that we want to use as a way to show how baseball works. We would like to add animations to the simulation but that is for another day. We have had a considerable amount of difficulty actually acquiring, compiling and cleaning data and another challenge is probably adding data for each position of the svg. The data is very sparse and spread out and every resource we encountered seemed to carry its unique flaws, adding a layer of complexity to our mission. Additionally, for the interactions, there will be lots of dependencies to consider as clicking on a section should trigger filtration of plots for different positions and perhaps players. The clicking of the svg is also nifty and very buggy. It seems there are a lot of kinks that need to be worked out especially when it comes to the interaction between the svg and the scrollable element. 
  </p>

</div>

<style>
    #writeup-container {
      background-color: #00a83b;
      width:100%;
      height:100%;
      position:fixed;
      margin: 0; 
      padding:0;
    }
    .button-container {
      display: flex;
      flex-direction: row;
      z-index: 100;
    }

    .buttons {
      height: 7vh;
      width: 10vw;
      border: 2px solid #422800;
      border-radius: 3vw;
      box-shadow: #422800 4px 4px 0 0;
      color: #422800;
      background-color: #fbeee0;
      cursor: pointer;
      font-weight: 600;
      font-size: 18px;
      text-align: center;
      border-radius: 2vh;
      line-height: 6vh;
      margin: 1vh 1.5vw 0px 1.5vw;
      z-index: 100;
      transition: background-color 0.5s; 
    }

    .buttons:hover {
      background-color: white;
    }
</style>