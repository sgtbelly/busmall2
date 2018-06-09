# busmall pseudocode
- create the repo
- create the md file for the user stories
- wireframe it and break it down, visualize 
- import images 
- display 3 random images from the assets
- give user 25 clicks
- choose one of the random images
- keep track of the number of times an image was clicked
- keep track of the number of times an image was displayed
- print out a report of data at the end
- need a way to represent an image
- in order to display an image what do we need to be able to do? 
- need a source...and an image element
- constructor function something like Photo 
- also need # of votes or selections.
- consider starting at 25 and working down
- chart.js is an object literal
////////////////////////// Demo Code \\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\

'use strict'

//array to store objects

Goat.allGoats = []

//constructor function

function Goat(name, filepath) {
this.name = name;
this.filepath = filepath;
Goats.allGoats.push(this)
}

//use constructor to create new goat pics

new Goat('Crusin goat', 'img/cruisin-goat.jpg');
new Goat('kissing goat', 'img/kissing-goat.jpg');
new Goat('sassy goat' , 'img/sassy-goat.jpg');

//listen for those events, something to be clicked all about events

var imgEL = document.getElementById('goat-pic');
imgEl.addEventListner('click', randomGoat);

//randomly display one of the pics

function randomGoat() {
var randomIndex = Math.floor(Math.random() * goat.allGoats.length)
imgEL.src = Goats.allGoats[randomIndex].filepath;
}

// counter

////////////////////// CSS Demo \\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
#goat-pic {

border: 2px, solid: yellow;


