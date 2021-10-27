---
layout: post
title: Bicycle-Powered Centrifuge
description: Open source prototype of bicycle powered centrifuge
---



An open source design of an easy-to-build and low tech centrifuge aiming at reducing the inaccessibility of lab equipment for low income biology labs and citizen scientists.

# A centrifuge ? What is this ?

If you have ever left muddy water in a container for a long time, you probably experienced this phenomenon. Under the influence of gravity, the dirt sinks to the bottom of the container because it is denser than water. Eventually, all the different components of the mixture are separated from each other based on their density in a process called sedimentation.

This process is widely used in biology to separate the different components of liquids, for example to separate cells from their growing medium, to purify DNA or proteins, etc.

However, this phenomenon takes a lot of time because the acceleration created by earth gravity is limited. That’s why biology labs use a device called a centrifuge. By spinning some sample at high speed, a centrifuge applies a centrifugal force that can be thousand times bigger than earth gravity. This force allows to sedimentate a liquid mixture faster and more efficiently.

# Ok fine, what's the problem then ?

Commercially available centrifuges are very expensive. Indeed, the cheapest one we found that fits the specification of our prototype cost over 3000€. Thus, low income biology labs and citizen scientists usually can’t afford a centrifuge that fits their needs, especially in developing countries. Even though open source DIY centrifuge projects already exist (Bhamla et. al, 2016; J. Albert, 2014; Sule et. al, 2019), they are generally designed for diagnosis purpose and thus either don’t allow centrifugation of large volume or can’t provide enough centrifugal force. This is a problem for research purposes, as the ability to centrifuge big volumes is not only less time-consuming, but it also allows producing more significant results by ensuring each sample received the exact same amount of centrifugation and limits the possibility of sample contamination.

# Our project : a bicycle powered centrifuge

This is where our project comes in. We proved the concept of using a bike to make a centrifuge that would be easy to build from accessible and cheap components and could centrifuge eight 50 mL tubes at the same time, and at a high centrifugal force.

Our main goals are : security because a centrifuge spins very fast and is dangerous, frugality so that labs with low resources can build it, and efficiency, so that it achieves the right speed and successfully sedimentates a cell culture.

<p align="center">
    <img src="/assets/images/centrifuge/3d_centri.png" width="95%">
    <i align="center">3d design of our centrifuge - adapted from T-FLEX CAD ST (CC BY 4.0)</i>
</p>

The rotation of the centrifuge is provided by pedaling on a bicycle. A 3d printed reduction gear is used to increase the rotational speed. We also created a tachometer to measure the speed of the centrifuge.

<p align="center">
    <img src="/assets/images/centrifuge/reduction_gear.jpg" width="95%">
    <i align="center">The 3d printed gear that provides the speed multiplication and the magnetic sensor of the speedometer</i>
</p>

# TIME LINE of the project

Week 1 : We decided on which project that we want to work, formed a team and attained different workshops, got prepared for our project.

Week 2 : We began and finished paper prototyping this week with cardboard, pitched our draft project to others and finished the 3D modelling for the week after.

Week3 : We dedicated to produce, test and improve. Likewise, we finished the wooden bike stand, the Arduino tachometer, the wooden baggage carrier and part of the centrifuge holder.

Week4 : We aimed to finish the POC, proof of concept. We assembled all components and used real sample (i.e., Escherichia coli) on it and tried to optimize it.

# Results

Our prototype was able to produce a maximum speed of 3000 rpm (1700 g) and was easily kept at 2000 rpm (760 g) for several minutes.

Our prototype in action

There's still a lot of characterization to do. However, at 2000 rpm for 7 minutes, the centrifuge successfully sendimentated E.Coli samples

# Thanks

We want to give credit to Zoe Pincemaille, who is the initiator of this project, under the direction of Ayan Abukar. She has assisted us with her expertise both on engineering and on the use of centrifuge in a biology lab environment.

This project was developed during the SDG Summer School at CRI, we thus also want to thank the mentors and organizers from makerLab, CRI in Paris who organized the workshops and gave us tremendous help with patience and especially Alexandre Singier.

# Are you interested in the project ?

There's still a lot of room for improvement before releasing the design for everyone. If you want to work on this project feel free to read the [technical documentation (WIP)](https://docs.google.com/document/d/1GKMS-Wq9Yjdb3quy89kQp21qidwZw9eGTthbY9N5ll4/edit?usp=sharing), you can also follow the project on [CRIproject](https://projects.cri-paris.org/projects/WbVtOeeV/des) and to see our prototype in action in the maker Lab at [CRI](https://cri-paris.org).

You can also contact us :

**Nicolas Aubourg** - Frontiers of Life Science Bachelor - CRI - University of Paris

nicolas.aubourg@cri-paris.org

**Shikhar Bhardwaj** - Design Researcher - Université Paris-Saclay

sgraphs@hotmail.com

**Huiyang Li** - Innovative Information system - Université Toulouse 1 Capitole

huiyang.li@ut-capitole.fr

**Jules Herrmann** - Frontiers of Life Science Bachelor - CRI - University of Paris

jules.herrmann@cri-paris.org