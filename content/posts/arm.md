+++
date = '2026-08-10T18:48:40+01:00'
draft = false
title = 'Arm'
description = 'Reflection halfway through internship'
+++

## Intro

When I started applying for internships half a year ago, Arm was probably one of the last companies I had in mind since I had only known it as a hardware company. Over the last couple of weeks I've come away with a new appreciation for the semiconductor industry, through my work on the Arm ML SDK for Vulkan. 

> **_NOTE:_**  Since the repo is open source, I'm free to share the commits that got merged.

## Onboarding

This was a pretty quick process, completing the required corporate modules, reading through the new starter guide for the team, and getting permissions for the repository. 

I was given a pretty small task - Implementing version flags to each component. This was pretty challenging, given that I knew basically no C++ prior to this internship and had just started learncpp at this point. Codex was a pretty good resource and surprisingly was able to have a really good understanding of the repo and was able to point me to the right places to start piecing it together. 

## First project

My first project was enabling support for KosmicKrisp, a translation layer that allows Vulkan to run on Apple devices where only the Metal API is exposed. This was a pretty good first project, as it allowed me to lean heavily into researching the topic rather than going straight into code, and gave me time to brush up on C++. It also kept me safe from much of the lower level details of the codebase, meaning that I could still apply simple high level reasoning to solve my issues. For example, I simply had to query if the current driver requested a certain extension and implement if so. 

## Initial thoughts

This first project gave me an appreciation for the robustness of a real codebase through CI. Each commit I made took nearly an hour to get through CI, and tested on many targets. As part of enabling this support I also played a role in enabling these tests to run on KosmicKrisp which was what allowed it to become introduced as an experimental feature. 

## Now 

I've spent a week or so finishing up my project and moving to my next goal: implementing CI 2.0. From what I've heard this was a pretty tedious process and a tool like this should help us be able to smooth things out. Pretty exciting that I got to be the one to create the file for the cli tool. 

I think the plan as I'm told is after spending the first month working on portability and finishing up the original project up early, to spend some time in between on CI (probably a pretty valuable skill, despite being a support activity), and finally a project working with the actual low-level implementation. Hopefully working on all three of these sets me up as best as possible for any future experiences. 

### Aside

Something interesting that's happened over the course of my internship is GPT 5.6. We get given a near limitless amount of Codex tokens, and as such I've been taking advantage. Its been quite a hard balance between not wasting time on syntax / looking through code and actually learning. Its quite hard to spend hours working on a simple fix when you know you have a tool that could do it instantly. 

Simply having it work and explaining what its done is also quite a trap. It's code is generally quite readable as is C++ syntax for anyone familiar with any language, and as such its easy to think that you would be able to do as Codex has eventually, but once actually having a go without it being completely lost. It is especially the ability for it to immediately have a good understanding of how things fit together that seems hard to replicate. 

I think my philosophy so far has been that I shouldn't be afraid to take full advantage of AI assisted coding, in combination with have it highlight the relevant sections and implementing any changes myself. In the time that I've saved using that assist I work on my own learning. Only a few days ago I did the coding assessment for Millenium where I was given a coding assistant (copilot) which was basically able to get through the whole task with little actual intervention on my side. 

But as I've grown my C++ skills greatly, and I shift towards CI work that is more Python centric, its time to start putting these skills to practice. One of the best advantages of doing an internship is that I get great senior devs who will happily critique my code and show me the light. I guess the reason why it was better just to have AI do the tasks was that I needed cover whilst I brushed up on fundamentals. But now, after I feel that I've shown my worth shipping impactful code I have more breathing room to start focusing on honing my skill. 

Overall, its been a great experience. 
