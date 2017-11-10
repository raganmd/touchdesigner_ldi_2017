# TouchDesigner Training | LDI 2017

## Overview
Join Matthew Ragan from Obscura Digital for a whirlwind tour of developing custom playback and generative systems. Over the course of two full days participants will learn the fundamental principles and organizational flow of working in Derivative’s TouchDesigner – for the uninitiated, TouchDesigner is a node based programming environment used in installations, live events, and museums internationally. This workshop will largely be focused on the intersection of art / design and the development of new tools for live performance. While there are a growing number of tools for media playback in live events, there are precious few for creating dynamic and generative artwork. In this workshop we will look at both how to playback traditionally made content, as well as how to build generative real-time rendered environments. Participants will also look at using existing modules in TouchDesigner for projection mapping applications large and small. More than just a flash and trash demo, this workshop aims to help familiarize participants with a development environment as well as examine the challenges and opportunities when designing real-time systems.

Participants can expect to walk away from the workshop with:

* an understanding the development environment
* best practices for development and organization
* foundational principles for playing and cueing traditional media
* foundational principles and experience creating generative artwork
* an overview of techniques for building user interfaces for interactive systems
* experience projection mapping with TouchDesigner
* an introduction to Python as a scripting language

## Target Audience

If turn key tools are out of your price range or lack the flexibility and adaptability you need for your media projects this might be the workshop for you. If you are an artist/designer/engineer that's looking for ways to engage with clients in ways that are outside of the bounds of traditional playback systems this might be the workshop for you. If you've been experimenting with TouchDesigner but want some direction in how to think about incorporating it into your larger workflow or project deployment, this might be the workshop for you. This workshop is built around beginner and intermediate concepts in working with TouchDesigner in installation / performance settings - no prior experience with TouchDesigner or Python is expected from participants.

## Getting Ready

As we speed towards LDI I hope you’re finding yourself excited about taking some time to learn more about TouchDesigner! Before you arrive, however, there are a few important things to keep in mind that will make the workshop run smoothly, and ensure you can focus on getting the most out of our time together. Below you’ll find a list of required first steps / tools to bring with you, and some recommended steps to help you prepare.

**Required**

* **Bring you Laptop** – Mac or PC. Make sure you review the [System Requirements](http://derivative.ca/wiki099/index.php?title=System_Requirements) from Derivative so you know you have a machine that’s TouchDesigner ready.

* **Don’t forget your power adapter** – TouchDesigner is largely a GPU based environment. This makes for fast operations, but often means that your battery will get consumed quickly. You’ll definitely want your adapter, even if it’s a pain to lug around.

* **[Download TouchDesigner 099](https://www.derivative.ca/099/Downloads/)** – it’s very important to make sure your machine can run TouchDesigner before you get to the workshop. There are some specific graphics card requirements and making sure everything works before the first day will make sure we can get the group started right away.

* **Get your TouchDesigner 099 License** – you can [register for a Derivative account here](http://www.derivative.ca/Login/RegisterForm.asp), and that will make sure you can create a non-commercial license key. The non-commercial license is free, and we won’t need anything more than this for our workshop.

**Recommended**

* **A 3 Button mouse** – You certainly can use a track pad while you’re working, but you’ll be much happier to have an actual mouse for working in Touch.

* **Download and Install a text Editor** – I like [Sublime](https://www.sublimetext.com/), but if you’re looking for free tools it’s hard to go wrong with [Visual Studio Code](https://code.visualstudio.com/)
[**Join the TouchDesigner Slack Channel**](https://slackpass.io/touchdesigner) – there are lots of great folks to chat with and learn from in here.

* **Bring some Assets** – You certainly don’t have to bring any extra assets, but it’s often nice to have more than just the stock images / videos handy.

* **Business Cards** – the best resources you’ll find at LDI workshops will be the other people in the room with you. If  you’ve got some extra business cards make sure you bring a stack to share with the folks in our group.

* [**First Things To Know**](https://www.derivative.ca/wiki099/index.php?title=First_Things_to_Know_about_TouchDesigner) – We’re going to cover a good chunk of what you’ll find in these videos and transcripts, but when it comes to learning something new repetition is no bad thing. If you’ve got some time to kill on the plane or in your hotel room you might browse the wiki a little to get yourself familiar with the TouchDesigner environment.

**Be Inspired**

* Take a look at some of the projects featured on the [Derivative Blog](https://www.derivative.ca/Blog/) to see what people are making and doing with TouchDesigner.

## Day 1 – Getting Started and Your First Project
*11.13.17*

Time| Topic
---|---
9:00| Introductions | Why use TouchDesigner | What TouchDesigner is and isn’t
10:00| Navigating the Environment
10:30| Building Networks | TOPs and CHOPs
12:00| Lunch
1:00| Procedural Geometry | SOPs   
1:45| Realtime Rendering - The Basics
3:00| Break
3:15| Realtime Rendering - Instances and Beyond
4:45| Q&A
5:00| Wrap Day 1  

### Overview of the Day
#### Navigating the Environment
Welcome to the TouchDesigner network. The Network is the name for the open space where we layout our nodes, and create chains of operators. We can zoom, pan, and navigate the network like a hierarchy. We can also expose lots of different viewports from here. We aren’t going to spend too much time talking about how to navigate the network abstractly – since it’s easiest to learn by actually working on a project – but it is handy to know a few things to help us get started.t

What is an operator?! If you’re familiar with Object Oriented Programming, we can almost think of our operators as an instance of an object. If you’re not familiar with OOP (I wasn’t when I started) that’s okay. We can think of an operator as a building block for our networks. How we arrange our building blocks changes what our final results are, and how we structure our projects can make it harder or easier at the end of the day to know what’s going on. In general, we are going to focus on building clean, modular, and reusable networks. It’s often tempting to feel like you need to make something unique for every show or installation, but in fact we end up being much happier programmers if we’re able to re-use pieces of our code.

“But Matt, forcing me to think about the engineering is going to hamper my creative process! I just want to create without boundaries.” Good for you. These days I don’t usually let myself be limited by what’s possible technically; however, when we’re starting to think about interactivity and developing new tools we need to start from somewhere – and our somewhere relies on making sure we have a common understanding of the computational processes and principles that will define what we can ask a computer to do. In designing a production we often wrestle with various constraints – the play is a constraint, the space is a constraint, the time, the set, and and and. Design is inherently a process of wrestling with constraint, so let’s think of our knowledge of this field as just another constraint for the time being. Rather than thinking of how we’re limited by the realities of current technology, we might instead think about how knowing the rules of a given system allow us to find ways of working around them or flat out exploiting them.

#### Building Networks
The connections of operators that we create in TouchDesigner are called "Networks." Just like Max has the convention of calling its work space a patch, and processing it's workspace a sketch, TouchDesigner follows in this pattern by giving it's workspace a name.

Networks primarily flow as streams of information between nodes of the same family. In Touch this is represented visually as objects/nodes/ops of the same color. Ops, short for operators, are our primary building blocks in this environment. Ops, from an abstract viewpoint, represent data types.
* **TOPs | Texture Operators** (purple) - represent texture / image information. 
* **CHOPs | Channel Operators** (green) - are arrays of values - if that sounds strange / new, we can also think of these ops as being list of numbers, just like a column or row in a spreadsheet. 
* **SOPs | Surface Operators** (blue) - are geometry data - these have all sorts of pieces tied to them, most importantly we need to think of them as spatial data.
* **MATs | Materials** (yellow) - are materials - these are used when we're doing realtime rendering.
* **DATs | Data Operators** (mauve) - are data operators - this is where we do all of our scripting and can enter data that's not an image, list, or geometry.

#### Procedural Geometry | SOPs   
Surface operators are an interesting wrinkle in the TouchDesigner family. Their history stretches back to before the fork from Houdini, and while there are some elements of SOPs that are a little cumbersome these days, they have tremendous potential. Over the course of this block we’ll pull apart a few of the usual kinds of SOP operations, as well as taking some time to visit some of the lesser know / discussed ops as we get a handle on what it is to build procedural geometry.

#### Realtime Rendering - The Basics
Realtime rendering is where it’s at. Some of the most fun to be had in TouchDesigner is working with realtime rendered content. That being said, there’s lots of ground to cover here. There are lots of similarities between touch and other rendering environments, and there are some unique pieces that are distinctly openGL related. All that being said, we’ll take time to look at rendering fundamentals as well as some of the gotchas that typically trip-up new touch programmers.

#### Realtime Rendering - Instances and Beyond
Rendering really gets interesting once we move away from just single objects and begin to think about lots and lots of objects. Instancing is just this kind of idea. Here we’ll find the flexibility to start to really create interesting explorations of realtime rendered content. There’s more than can be covered in a single day, let alone a few hours, but we’ll still do our best to at least debunk what’s really happening under the hood and have a solid set of understanding this essential realtime rendering concept.

## Day 2 – Realtime Rendering and Mapping
*11.14.17*

Time| Topic
---|---
9:00| UI Building | Components
9:30| Python Fundamentals - Understanding where Python fits into Touch
10:00| Making a Video Selector with Presets | Working with Python
11:30| Planning for future module integration
12:00| Lunch
1:00| Mapping our Content | Overview and Frame
1:30| Stoner | Kantan Mapper | Cam Schnapper
3:00| Break
3:15| Setup for Live Events and Show Ready
4:45| Q&A
5:00| Wrap Day 2

### Overview of the Day

#### UI Building | Components
UI Building is a strange beast in TouchDesigner. It’s difficult to say if there are right or wrong ways to tackle this process, but there are certainly ways we can make this process less cumbersome. We’ll look at some of the default UI building elements, as well as how to make our own during this block. Later in the day we’re going to return to this and really explore what it takes to build a UI, but for now we’ll just get our bearings.

#### Python Fundamentals - Understanding where Python fits into Touch
Python is one of the fastest ways to level up your TouchDesigner game. There are few things you can’t do in Touch with Python, and while there are efficiency trade offs to consider, there are also lots of exciting ways we can extend and expand our reach. We’ll talk a little bit about how to read the documentation, and look at where Python fits into the grand scheme of things.

#### Making a Video Selector with Presets | Working with Python
Finally, we’re going to start building an app. At this point we’re going to take all of things we’ve learned and experimented with and build something functional. This is a little shy of the app you might want to build for an event or installation (in fact it’s probably pretty far off the mark), but we need to start somewhere. This will also give us some insight into how Python works in conjunction with our op workflow.

#### Planning for future module integration
Before we break for lunch we’ll take a moment to talk through how we plan for future additions. Many Touch programmers often have their sights set on that holy grail of a perfect network. That’s good, and we can do a healthy bit to think through how we plan for the future, for refactoring, and for collaboration.

#### Mapping our Content | Overview and Frame
Before we dig into doing any actual mapping, we need to first talk about mapping methodologies. We’ll take a moment to discuss some of the larger considerations for projection mapping, and how we might want to consider our approach.

#### Stoner | Kantan Mapper | Cam Schnapper
Now that we’ve built our own piece of the puzzle, let’s look at how we can integrate some ready made tools for mapping. We’ll consider three different big-idea approaches for mapping, what they’re good for, where they fall down, and when we might choose to use which one.

#### Setup for Live Events and Show Ready
Rounding out two full days we’ll revisit how we need to consider app building with TouchDesigner, considerations for making sure we’re show ready, and some tips and tricks to help you work smarter not harder. Then, all too quickly, it’ll be time for us to pack up and move on to our next LDI adventures.