# tessel-node-red
A library that allows users to get Node Red working with Tessel and it's module ecosystem.
Node Red is an IBM open-source project for visual representation of programming. Similar in concept to Scratch, it provides a visual representation of inputs, outputs, functions and so forth as draggable and droppable nodes in a workspace, and users can re-use the codes for other projects.

Tessel Node Red was created to help ease young learners into the world of microcontrollers. However, it can also be used by hobbyists and experienced makers alike to program their projects.

How It Works
You can create your own nodes in Node Red. It requires 2 files - an HTML file that stylise and define the node templates, and a corresponding JS file with all the necessary code snippets. 

To install the Tessel node red files, you need to first install Node Red. 

# Install
Follow these steps to get Node Red installed and ready to go:
 
1.	npm install node-red
2.	node-red

For more information on how to install Node Red, go to http://nodered.org/docs/getting-started/.

#Setup
Once installed, you can start the node-red server with node-red and point your browser to http://localhost:1880.
If it is showing up in your browser, congrats! Press Ctrl-C to stop node-red. We'll come back to it with tessel nodes....be patient.

For Tessel setup, go to the folder where node-red is installed. It should be found in your /node_modules/ folder in your system.
cd node_modules

Inside this folder, install tessel.
npm install tessel
 You may need to do a sudo if it doesn't work.
 
You should see both tessel and node-red folders.

Next, you have to place the tessel.html and tessel.js file in the node-red subfolder where all the node files are stored.

cd node-red/nodes/core/hardware

You will see some existing hardware files for Arduino,gpio. Copy and place the tessel html file and js file here.

#Run
Once done, go back to the node-red root folder
cd
cd node_modules/node-red
node red.js

You can do a node red.js -v for verbose mode to see if the files are loading correctly.Great for debugging.

Go to your browser localhost:1880 again. You should be able to see new nodes for tessel at the bottom left column.

#Issues

As I am quite a noob, here are the current issues :
The JS and HTML files as of today are not working, i.e, you can see the nodes and dialog boxes ( I adapted heavily from the Arduino Firmata sample), so I need experts out there to help get it right.
#To Do
Propose a framework of what nodes should be created for the Tessel family of boards and modules.
- currently we only npm install what we need for each module, e.g, ambient, climate etc. 
- I don't think we can have a generic Tessel In node. So perhaps we should create node templates for each node should we need to do settings for each module.
- Similar for Tessel Out and Tessel Base board.
Schema 
For each board, there are ports and a gpio bank. Tessel 1 has 4 ports, 1 gpio bank with digital, analog and PMV pins. Tessel 2 has ethernet, usb 2.0, 2 ports, and a gpio bank. also, there is a micro-usb for power and input/output. So, we can create 2 Tessel Board nodes for each model.
For modules, we need to specify which port the module is plugged in to. A drop down of A, B, C or D (omit C for modules like camera), or GPIO pin no. This will be passed to the script portion to define the module?

There are lines like "portlist" and "pins" in the arduino-firmata script, which I suppose has a similar setup as Tessel. Tried looking through the tessel scripts and js files....beyond my abilities to sense-make.

I think the first test is to do the blink test from node-red. Drag a Tessel 1 node as output, and an inject as origin/input. Deploy it by passing "tessel blink" as msg.payload. If it connects and blinks, it should be ok...i.e. Hello World from Node Red works.
#NEW
Realised after reading the examples on Beaglebone and Raspberry Pi, I got it wrong. Need to deploy Node Red on Tessel instead on on localhost of terminal/computer. So, doing 127.0.0.1:1880 won't work. 
It has to be on something like http://tessel.localhost:1880.  And this is started on command line like node-red-pi...at least on the examples. 

Maybe we need to look at  http://nodered.org/docs/embedding.html to figure out on Node Red side? 

Anyone?

# Examples
Here is some example setup/pics/code etc to get a basic example running with Node Red.

# Contact
Having an issue with any of this? Check out [the forums](https://forums.tessel.io/) and ask for help!
