---
layout: post
title: Subway crowd cellular automata
description: One week modelisation project
---

As an assignment in my program, we had to do a full modelisation project in **only one week**.

The project turned out to be quite challenging given the time we had. However, I still think it was a very interesting learning experience.

<table>
<tr>
 <th scope="col">
 	<img src="/assets/images/subway-crowd-cellular-automata/dynamic-1.png" width="95%">
 </th>
 <th scope="col">
 	<img src="/assets/images/subway-crowd-cellular-automata/dynamic-2.png" width="95%">
 </th>
 <th scope="col">
 	<img src="/assets/images/subway-crowd-cellular-automata/dynamic-3.png" width="95%">
 </th>
</tr>
</table>
<p align="center"> An example of dynamic we wanted to model</p>

# Abstract

The location of agents in a subway wagon are subject to complex dynamics : people want a comfortable place while avoiding proximity to other people. Added to the constant flow of subway users entering and exiting the wagon, these dynamics results in more or less efficient flow of people.

During this one week modelisation project, we want to model the flow and distribution of agents evolving in a subway wagon to study the impact of the geometry of subway (position of seats and metal pole) on the flow and the final distribution of agents as well as the number of users that were able to find a comfortable place.

We propose a cellular automata model describing the interaction between agents, walls of the metro, seats, and rest position (ie. next to the walls and to the metal poles).

<p align="center">
    <img src="/assets/images/subway-crowd-cellular-automata/comfort-matrix.png" width="50%">
    <br />
    <i align="center"></i>
</p>

# Links

Our poster can be found [in pdf format here](/assets/pdf/modelisation-week/Poster Subway dynamics.pdf).

Our final report can be found [in pdf format here](/assets/pdf/modelisation-week/Final_report_team3.pdf).

Code for our small python package, code for data analysis, images and documentation (basically everything) are on this [github repository](https://github.com/drblobfish/subway-crowd-cellular-automata).

More information can be found on our [CRI project page](https://projects.learningplanetinstitute.org/projects/1ploTJ6e/des).

# Context

This one week long project is produced as an assignment during the Modelisation Project Week in the [Frontiers of Life Bachelor](https://licence.learningplanetinstitute.org/fr) (Center for Interdisciplinary Research, University of Paris), with Antoine Bergel and Anton François as Teachers.