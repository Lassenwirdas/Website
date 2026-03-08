---
title: IVAR'26 - Implementing the techniques
summary: A summary of the implementation process, techniques, hurdles and the AI experience.
date: 2026-02-01
cardimage: photo2_card.jpeg
featureimage: photo2.jpeg
caption: ":tada:"
authors:
  - Lasse Medla: author.jpeg
---

The implementation process was unusual in the case, that we had to complement an existing project structure with our own ideas.
The first steps of my jurney was the rudimentary conceptualisation -- see [Post IVAR'26 - Conceptualizing the desired Locomotion Techniques]({{< ref blog\post1\index.md>}}) for reference, before I tried to boot up the project for the first time. 

Doing that gave me a rude awakening: The general Meta-Structure was seemingly not compatible with the project structure anymore. So I was forced to redo the player logic and started implementing, hoping I could rewire the complete logic later. Subsequently running into more and more problems, and resorting more and more to external knowledge resources and AI, I came to the point where I started to desperately tried everything suggested without questioning it, ultimately ruining what I had so-far completely.

In the lecture the Professor, whilst holding our usual weekly report, then asked about our AI usage and questioned, to what extend the newer Models would be capable of finishing certain IVAR-Tasks. Inspired by this, and with the realization I had to start from scratch anyways, I had a new goal: How far could I go, mimicking a clueless beginner and letting AI do all the rest.

The Vibe-Coding approach was not fun at all to watch or whitness as a CS-Major, but yielded promising results pretty fast. The general logic and pjoject structure was picked up by the model (GPT 5.0 R on Perplexity Pro) reasonably fast, and the depth and accuracy of requested explanations were adequate. The main work was done in about one workweek, but the tweaking was a whole other story. The limits of the model, especially in rewgard to the memory of it, became brutally clear while trying to tweak the experience. Simple tasks, combined with faulty memory lead to constant errors, forcing me to backtrack time and time again, before finally reaching a presentable State.

Quick Timeline:
- loading the Files and explaining the parcour to the AI
- dumping my ideas and visions int the agent
- asking for the best approach
- instructing the AI into the full guidance set
- resort to only communicate inputs and results to each other, becoming a medium and only occasionally complementing with more directional input.

The biggest hold-up were misunderstandings and memory loss, forcing rewinds and redos over and over again. Especially for restricted users this could prove desastrous, for they would have to redo the priming of the LLM over and over again to improve their results.

While preparing the presentation and completing the Parcour I stumbled across another Problem: Not taking into account the inner structure of the project led to a decoupling of the parcour triggers with my locomotions. The inheritances were scewed and not fixable without major overhaul, that got deemed to risky days before the presentation[^problem]. Luckily my conceptualized failsave proved itself to be sufficient for that matter, for one could always revert into the legacy locomotion to trigger the mechanics, that could not be triggered with my techniques.

The walkthrough with the PresentationState of the Project can also be found on [YouTube](https://youtu.be/sv-bMEMf96g).

The complete Chat-History of the Project can be found in the following Download-Links
- [Chat1 herunterladen (PDF)](Chat1.pdf)
- [Chat2 herunterladen (PDF)](Chat2.pdf)

Note: As stated i mimicked a beginner, asking beginner questions, behaving like a beginner and not caring about typos etc.. Could you do better? Probably yes. Could you optimize that? Most definetly, but that was not the goal here and is rather subject to a future research Project.

[^problem]: The Problem was, that the legacy locomotion should have been the one to be altered into our desired technique and therefore all the dependencies were hardcoded into the technique. That rather unfortunate design led to my techniques being completely unattached from the parcour logic. Theoretically, that could be fixed with overhauling the dependencies and or redoing the legacy technique, but I saw it as an opportunity to force locomotion switches and deemed it acceptable.