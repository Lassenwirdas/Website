---
aliases:
  - /blog/semester-ws2627/
title: "Winter Term 26/27 - Satellite Fixer"
subtitle: "Third semester, four people and a broken satellite in orbit :satellite:"
summary: An overview of my current Master's semester and its main project, Satellite Fixer - an asymmetric co-op serious game in which an astronaut in VR and an operator at mission control repair a real ESA satellite together.
date: 2026-10-19
caption: "Semester 3 of the M.Sc. - in progress"
---

<!-- TODO: Präzisieren - persönliche Eindrücke, Fortschritt zu Alpha/Beta, Screenshots, Netzwerk-Entscheidung -->

## The semester at a glance

The winter term 2026/27 is my third semester in the Master's program and the first one in which I balance my studies with my working student position at GRAYOAK from day one.

After Mix-Mal, I am staying with serious games: the central project of this semester is **Satellite Fixer** (officially *P04a - Collaborative Satellite Repair*), a group project in the *Serious Games* course at TU Darmstadt. This post is a living document - I will update it as the project progresses.

## The idea

Satellites are everywhere in our daily lives - weather forecasts, navigation, communication in a crisis - yet very few people know how they are built or how they actually work. At the same time, the European space industry keeps growing. Satellite Fixer wants to close that gap through play.

The game is an **asymmetric co-op for two players** who have to bring a broken satellite back into operation:

- **The astronaut (VR, Meta Quest 3)** floats in space next to the satellite, searches for the source of the fault, carries out the repair and reports back what they see.
- **The operator (PC)** sits in a mission control centre - think ESA. They have the mission data, the sensor readings and a digital handbook, figure out what went wrong and guide the astronaut through the repair.

The twist: each player sees different information. Neither of them can solve the problem alone, so they have to talk to each other. Both players sit in the same room and communicate directly, without any in-game voice chat, while the game state is synchronized in real time between the VR headset and the PC.

From level to level, the players meet different **real ESA satellites**, each with its own look, purpose and sensors. The 3D models come from [ESA SciFleet](https://scifleet.esa.int/), and faults occur at random, so no two rounds play out the same.

## Who it is for

The game is designed to be played at the **DLR School Lab Darmstadt** by kids and teenagers from **grade 8 upwards** who are interested in science and technology. The content builds on what they already know from school physics, especially the introduction to electricity.

There are two learning goals:

1. Basic knowledge about real satellite programmes and the technology behind them.
2. Focused communication and cooperative problem solving when everyone holds a different piece of the puzzle.

That second goal is what I find most interesting about the concept: the communication between the players is not a side effect of the game - it *is* the game.

## Team and my role

We are a team of four - Hussain, Joshua, Max and me - and split the work into work packages:

| Work package | Lead |
|---|---|
| Management & coordination, interface, environment | Max |
| Network (host, VR connection, game state sync, error handling) | Lasse |
| VR gameplay (movement, satellite & sensor interaction) | Hussain |
| PC gameplay (scenarios & game state management) | Joshua |
| Network menu and menu functions | Lasse |

My part is the **network layer**: making sure the PC app (host) and the VR app (client) always agree on the state of the game, that repairs done in VR arrive at mission control, and that the whole thing recovers gracefully when the connection hiccups. Coming from IVAR'26, where I was fighting the Meta setup on my own, it is a nice change to own one clearly defined piece of a bigger system.

## Technology

- **Engine:** Unity 6 with the Universal Render Pipeline
- **XR:** OpenXR and the XR Interaction Toolkit, starting from Unity's VR Core template
- **Devices:** Meta Quest 3 for the astronaut, a Windows PC for the operator
- **Architecture:** one Unity project with two scenes. The PC app is the authoritative host; the VR app is the client and only sends repair attempts, which the host checks.
- **Content:** satellites, sensors and faults are defined as data (ScriptableObjects), so new levels can be added without touching code.

Gameplay code never talks to the network directly - everything goes through a small sync abstraction. For now, a local loopback lets us test both roles in a single editor scene; the real network transport is the next big decision for my work package.

## Current status

The concept is written, the repository is set up, and a first code skeleton for the shared game state, the operator and the astronaut side exists. Open questions we still have to settle as a team include the network transport and how the headset finds the PC, which satellites and faults go into the first scenarios, and how to move around in zero gravity.

The project is open source - you can follow along on [GitHub](https://github.com/Lassenwirdas/SatteliteFixer).

| Milestone | When |
|---|---|
| Alpha | mid/late December 2026 |
| Beta | late January 2027 |
| Final version | February 2027 |
| Final presentation | early March 2027 |
