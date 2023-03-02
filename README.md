# samosa
Lab 2: Samosa Selector
# Overview
In this lab, you will create a game called Samosa Selector that is based on an incremental game called Cookie Clicker. The goal of the game is to produce as many cookies by clicking on the Big Cookie as you can. However, in this version, instead of clicking a cookie, the user will be selecting a delicious samosa.

# Gameplay
The game starts out with the user having zero samosas. When the user clicks the Big Samosa, it initially produces one samosa per click. Then,

--When the user has 10 samosas, they can buy a Double Stuffed upgrade, which produces double the amount of samosas per click.
--When the user has 100 samosas, they can buy the Party Pack upgrade, which produces 5x the amount of samosas per click.
--When the user has 1000 samosas, they can buy the Full Feast upgrade, which produces 10x the amount of samosas per click.

The game continues on forever and the user can continue to gain gigantic amounts of samosas. Yum!

View an exemplar of what you'll be creating in this lab here!

# Required Features

The user can click on the large samosa to increase their samosa count by 1. There are three available upgrades -- Double Stuffed, Party Pack, and Full Feast -- that the user can purchase to increase the number of samosas per click.

--A large samosa that the user can click to harvest one samosa at a time
--A counter displaying the number of samosas the user currently has
--Three upgrades that increase the effectiveness of the user’s cursor at certain point thresholds

When purchasing an upgrade, the user loses samosas from their total count. There is also an added "pulse" effect to the samosa that shrinks the large samosa when clicked and grows when hovered over.

--When purchasing an upgrade, the user loses samosas from their total count
--Decrease the scale of the large samosa when the user clicks the samosa to create a pulse effect

# 🎯 Goals
By the end of this lab you will be able to...

--Use useState hook to create a state variable and a function that is used to update the state
--Register an onClick event to a button in a React project
--Define event handling functions in a React project

# Resources
--Vite: Getting Started
--ReactJS: Using the State Hook
--W3 Schools: React Events
--ReactJS: Handling Events

# Lab Instructions
Required Features

Step 0: Create a New React Project Using Vite
In this step, we will create a new React project using Vite and remove some of the provided starter code.

--Open the Terminal and navigate to your Github repository.
--In your Github repository, create a new Vite React project called '''samosa-selector'''. As a reminder, the command to start a new Vite project is:
'''
  npm create vite@latest
'''
--Open your project in Visual Studio Code
--Replace the provided starter code in App.jsx with the following code:
'''
import './App.css';

const App = () => {

  return (
    <div className="App">

    </div>
  )
}

export default App
'''

#📍 Checkpoint 0: At this point in the lab, your app should look like a blank page like this (your app may have a white background depending on your browser settings):


Step 1: Create the User Interface

In this step, we will create a basic user interface for the game.

In App.jsx:

-In the <div className="App>" create the following nested elements:
--A <div> with the className="header" with the following nested elements:
---An <h1> with the title "Samosa Selector"
---An <h2> with the text "Count:"
---An <img> with the className="samosa" and src set to an image of a samosa (use one from the internet for now).

Add some style to the interface using CSS:

-Create a style rule in App.css for .samosa with the following rules:
--Set the height of the image to 15em
--Set the padding of the image to 1.5em
--Set the margin to 0 auto
--Set the text-align to center

If your app has a light background and you would prefer a dark one:

-Locate and delete the @media (prefers-color-scheme: light) section in index.css

#📍 Checkpoint 1: At this point in the lab, your app should look like this:

Step 2: Add a Counter

In this step, we will create a state variable to keep track of the number of clicks.

In App.jsx:

-Check that you have imported the '''useState''' hook from ''' 'react' '''
'''import { useState } from 'react';'''
-Using the '''useState()''' hook, create a state variable called ''' count '''with a value of 0. This state variable will be used to keep track of the number of total clicks.
'''const [count, setCount] = useState(0);'''
-Using the '''useState()''' hook, create a state variable called '''multiplier''' with a value of 1. This state variable will be used to keep track of the current number of samosas per click.
'''const [multiplier, setMultiplier] = useState(1);'''
-Define a function called updateCount() that sets the value of the state variable count to it's current value plus multiplier when called.
'''const updateCount = () => setCount(count + multiplier);'''
-Set the updateCount function as the onClick event handler for for the <img> element displaying the samosa when it is clicked.
'''<img src="/samosa.png" className="samosa" onClick={updateCount} /> ''' 
-In the '''<h2>''' tag, call the count state variable to display the number of clicks.
'''<h2>Count: {count}</h2>'''

#📍 Checkpoint 2: Your app should now keep track of the number of samosas when the user clicks the image of the samosa. At this point in the lab, your app should look like this:

Step 3: Add Upgrades
In this step, we will add three upgrade options to the user interface.

Name	              Description	   Cost
Double Stuffed 👯‍♀️	2x per click	 10 samosas
Party Pack 🎉	     5x per click	  100 samosas
Full Feast 👩🏽‍🍳	    10x per click	 1000 samosas

In the '''<div>''' with the class name '''App''' add the following:

-A <div> with the className="container" with the following nested elements:
--For each upgrade, create a <div> with the className="upgrade" that contains the following nested elements
---An <h3> heading with the name of upgrade
---An <p> with a description of the upgrade
---A <button> with a label with cost of samosas needed to apply the upgrade

Add some style to the interface using CSS.

-Create a style rule for '''.container''' with the following rules:
'''
.container {
  margin-top: 50px;
  display: flex;
} 
'''

Create a style rule for .upgrade with the following rules:
'''
.upgrade {
  border: 1px solid rgba(153, 153, 153, 0.497);
  border-radius: ;
  padding-top: 20px;
  padding-left: 10px;
  padding-right: 10px;
  padding-bottom: 20px;
  margin-right: 25px;
  width: 200px;
  line-height: 0.5;
}
'''

Create a style rule for button with the following rules:
'''
button {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.3em 1em;
  font-size: 1em;
  font-weight: 500;
  font-family: inherit;
  background-color: #1a1a1a;
  color:  rgba(255, 255, 255, 0.87);
  cursor: pointer;
  margin-top: 10px;
}
'''

#📍 Checkpoint 3: Your app should display the three possible upgrades. At this point in the lab, your app should look like this:

Step 4: Handle Upgrades

In this step, we will add event handlers to the button of each upgrade. If the user has enough samosas, the upgrade changes the threshold of the multiplier state variable.

-Define a function called buyDoubleStuffed() that sets the value of the state variable multiplier to two times its current value if the current number of counts is greater than or equal to 10.
'''
const buyDoubleStuffed = () => {
  if (count >= 10) {
    setMultiplier(multiplier * 2);
  }
}
'''
-Set buyDoubleStuffed() as the onClick event handler for the <button> labeled 10 samosas.
'''
<button onClick={buyDoubleStuffed}>10 samosas</button>
'''
-Define a function called buyPartyPack() that sets the value of the state variable multiplier to five times its current value if the current number of counts is greater than or equal to 100.
'''
const buyPartyPack = () => {
  if (count >= 100) {
    setMultiplier(multiplier * 5);
    setCount(count - 100);
  }
}
'''
-Set buyPartyPack() as the onClick event handler for the <button> labeled 100 samosas.
'''
<button onClick={buyPartyPack}>100 samosas</button>
'''

-Define a function called buyFullFeast() that sets the value of the state variable multiplier to ten times its current value if the current number of counts is greater than or equal to 1000.
'''
const buyFullFeast = () => {
  if (count >= 1000) {
    setMultiplier( multiplier * 10);
    setCount(count - 1000);
  }
}
'''

-Set buyFullFeast() as the onClick event handler for the <button> labeled 1000 samosas.
'''
<button onClick={buyFullFeast}>1000 samosas</button>
'''

#📍 Checkpoint 4: At this point in the lab, your app should look like this:


🎉 Congratulations, you've completed your first lab! 🎉

If you have time left over, continue on to the stretch features to customize and improve your app!


# Stretch Features

Step 5: Reduce Samosa Count After Upgrade Purchase

In this step, we will update each of the event handling functions so that the user loses samosas from their total count for the upgrades they purchase.

Using setCount(), reduce the count state variable by 10 when the user purchases a Double Stuffed upgrade.

💡 Hint
To reduce count by 10, we write setCount(count-10) in the buyDoubleStuffed() event handler.
Note: This code snippet should be included within the conditional statement that checks whether the user has at least 10 samosas to avoid creating a negative balance.

Using setCount(), reduce the count state variable by 100 when the user purchases a Party Park upgrade.

💡 Hint

Using setCount(), reduce the count state variable by 1000 when the user purchases a Full Feast upgrade.

💡 Hint
📍 Checkpoint 5: At this point in the lab, your app should look like this:

Step 6: Change Size of Samosa on Hover and Click

In this step, we will add CSS to transform the samosa to grow when hovered and shrink when clicked to create a "pulse" effect.

Create a CSS rule for the .samosa:hover that:

Sets the cursor property to pointer
Sets the transform property to scale(1.1)

Create a CSS rule for the .samosa:active that:

Sets the transform property to scale(0.95)
📍 Checkpoint 6: At this point in the lab, your app should look like this:

Screenshot of app with stretch feature two implemented

🎉 Congratulations 🎉

You've completed your first lab AND stretch goals! 🚀

💡 TIP: Remember to come back and reference this lab when you need to do similar things in your project!
