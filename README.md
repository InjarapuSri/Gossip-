# Gossip 
In this project I have implemented gossip protocol and achieved convergence with concurrent  processing for four different topologies.

The goal of this project is to determine the convergence of such algorithms through a simulator based on actors written in F#. Since actors in F# are fully asynchronous, the particular type of Gossip implemented is the so called Asynchronous Gossip.

**Gossip Algorithm for information propagation** -  The Gossip algorithm
involves the following:

* Starting: A participant(actor) it told/sent a roumor(fact) by the main process
* Step: Each actor selects a random neighbor and tells it the rumor
* Termination: Each actor keeps track of rumors and how many times it has heard the rumor. It stops transmitting once it has heard the rumor 10 times.

**Push-Sum algorithm for sum computation**
* State: Each actor Ai maintains two quantities: s and w. Initially, s = xi = i and w = 1
* Starting: Ask one of the actors to start from the main process.
* Receive: Messages sent and received are pairs of the form (s, w). Upon receive, an actor should add received pair to its own corresponding values. Upon receive, each actor selects a random neighboor and sends it a message.
* Send: When sending a message to another actor, half of s and w is kept by the sending actor and half is placed in the message.
* Sum estimate: At any given moment of time, the sum estimate is s/w
where s and w are the current values of an actor.
* Termination: If an actors ratio s/w did not change more than 10−10 in 3 consecutive rounds the actor terminates. WARNING: the values s and w independently never converge, only the ratio does.

**Topologies** The actual network topology plays a critical role in the dissemination speed of Gossip protocols. As part of this project you have to experiment with various topologies. The topology determines who is considered a neighboor in the above algorithms.
* Full Network: Every actor is a neighbour of all other actors. That is, every actor can talk directly to any other actor.
* Line: Actors are arranged in a line. Each actor has only 2 neighbors i.e. one left and one right, unless it's the first or last actor.
* 3D Grid: Actors form a 3D grid arearranged in the form of a 3D grid and can only talk to the neighbour in the grid.
* Imperfect 3D Grid: Imperfect 3D grid is same as 3D grid except that each actor will be connected to the neighbours in the grid plus one random neighbour in the grid.

