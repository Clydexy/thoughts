+++
date = '2026-08-15T23:14:35+01:00'
description = 'My journey of winning my first hackathon as a high schooler'
draft = false
italic_title = true
title = 'to win a hackathon'
+++

[Report](https://docs.google.com/document/d/1zQhEKW8GKSJVNZ_vL-Nay2dnsQWwmlcajMAJzb_zEgk/edit?usp=sharing)

## Buildup

This was my first ever hackathon, and as such it was pretty exciting. The format was a one-week development period (keep in mind this was prior to AI being able to code well) and the goal was centered around one of the UN SDGs, quality education. 

Obviously, AI being a big topic we quickly decided on trying to bring AI into our project somehow. Ultimately we decided on building an app that would have as many features as we could think of, and wow the judges with the sheer scale and functionality of our app. This was also massively parallel, with each of us being able to work on a different component (Automatic quiz generation, RAG chatbot, automatic lecture summarizer). 

I also realised pretty quickly that in order to present this, we would need a flagship feature that we would focus on the most, in order not to leave the judges confused as to what exactly our app did. While most of the other features were simply API wrappers (though some of these seem to have become actually popular such as lecture summarizers on every student's instagram ads), I thought it was best to make our app some sort of ecosystem. One where the students learning was not isolated from the school, and as such made our EdTech product B2B and targetted towards schools, something that seemed quite on trend and underutilised by EdTech startups who sell these mostly to schools. 

This ecosystem eventually manifested in a Google Classroom style format where students would be able to join classrooms hosted by teachers, and where teachers would deposit their materials and students would be able to then access these materials, as well as the teacher then being able to see summaries of student pain points with the lecture materials. Students would be incentivised to use it due to its much greater of the specific class material, and teachers would be incentivised to upload their slides to be able to guage the classes progress.

## The sprint

Full-stack development as a beginner was not easy. While I had experience both in python and swift, I had no experience actually dealing with server setup, cloud infrastructure, and even raw requests, having been shielded by libraries. We actually learnt about the idea of setting up a computer in the cloud by one of our friends leaking a competitors site's IP address, where after checking whois revealed that we should look into Digital Ocean. Looking back, how did we not know that it was as simple as setting up a free AWS EC2 instance.. 

We learnt most of flask from inspecting one of our team member's previous project's source code, where we just copied the request handler decorator syntax. Looking back now this would have been so easy as just a serverless function. 

Also, we had to adapt to the new declarative SwiftUI, after many years of working with UIKit and storyboarding. I definitely can't complain about its syntax, though the simplicity concealed a complete rethink of how we implemented functions especially moving from Model View Controller to a Model View ViewModel paradigm. 

We also had school during this time, so many classes were spent working on the code whilst the teacher was not looking. We stayed in our senior common room till nearly 6-7pm every night that week. Fun times. 

## The competition

Overall this went pretty well. We started off presenting in stalls, where we didn't really draw that much attention from normal storegoers. Our initial idea was to use phone stands to present our phones much like an Apple Store, but couldn't secure any in time, and as such couldn't really compete with massive hardware-based projects like an arcade game stand. 

Eventually some of the judges came around, where we emphasized our ecosystem-based approach, and showed them the scale of our project. This was also quite early into AI, so we were still relatively unique and novel in integrating this and received a positive reaction from most judges. 

The main reason why we came to this competition was because it was sponsored by Microsoft. They had sent the Asia CMO to judge our competition, but when the organisers began asking us to assemble in the hall it became clear that we would miss the chance to present to him directly. But, one of my teammates in his infinite sociability had managed to speak to him in the morning before we arrived, and spotted him as we were about to leave. We asked him if we could give him a quick presentation, and were the last group remaining and pitching him specifically. He was extremely enthusiastic about our project, and it was clear he would be a great ally. 

On stage in the finals, we delivered a decent presentation, but what sealed the deal was the fact that one of our teammates as Student Council president had brought up our project to the school principal, and we would take full advantage of this opportunity. We consistently mentioned our action plan in deploying this to schools, and as one of the last presentations we had noted down every question they had asked other teams, and when the same questions came around were fully prepared. 

We won.(We got money and an internship at a startup together! Oh and the Linkedin of the CMO of Microsoft Asia!) 

## The aftermath

Riding the waves of victory, we decided to bring our project to production and deploy with students in our school. We already had an ongoing conversation with the principal, whereafter we started a conversation with our head of IT, who was already quite interested in these tools. 

This time, we were much more prepared, and planned to rebuild it right. First, we stripped down our project. We wouldn't be able to deploy a full suite of tools at production quality. We then looked into our killer feature, as the judges had coined it. The interaction between teacher and student in this ecosystem. We identified a pretty interesting educational theory: Constructive Alignment. 

The idea is that we build the student to construct their own version of this knowledge by deriving it with the help of the teacher, and then align this construction to the reality. We thus created a system wherein the teacher creates assignments for their students on our platform, which get broken down into multiple learning objectives (e.g. identify ionic compounds from name, describe properties of ionic bonds, ..). We can then have the student converse witht he AI agent and have them explain each idea (construction) and have the agent correct their misconceptions (alignment). We have a full technical report here: [Report](https://docs.google.com/document/d/1zQhEKW8GKSJVNZ_vL-Nay2dnsQWwmlcajMAJzb_zEgk/edit?usp=sharing)

Ultimately, we trialled the project with around 70 students with a few teachers that we were close to. The results were mixed, with the noise in data being too hard to draw a significant conclusive result, and adoption not being widespread given that my teammate and I shifted our focus towards our final exams. We did however plant this idea into our IT teacher's head and convinced the school leadership into a partnership with MagicSchools, a SaaS that was similar to our intitial hackathon project in that it was a collection of tools that educators and students would be able to use. 

In terms of the technicals: this time we did it properly. We completely rewrote our flask code with Python OOP, making our code much tidier and more robust to edge cases. We implemented rate limiting with a redis instance. We also set up MongoDB with orchestration from Docker Compose. By Dockerising each container, though not autoscaling allowed us to shorten our development cycle and set up simple local networking between our database containers and our server container. We also used the new AI tools at the time that were only good at frontend to create some high quality website designs, where we discovered that we could implement streaming so that students would not be stuck staring whilst the whole text response loaded as in the demo. 

This also led me down a rabbit hole of new RAG research in terms of Knowledge Graphs. I mocked up a few prototypes that used one of the cheaper models to perform Named Entity Recognition(NER) and structure data into these Knowledge Graphs. I did this on one of our textbooks, and through the Neo4j visualisation noticed that it did particularly well perhaps due to considerable exposure to high school level topics in pre-training. An interesting exercise would have been in fine tuning it to be even better. This was extremely promising as one of the main issues with our system so far is that it relied far too much on the model's endogeneous knowledge which strayed away from the syllabus and would explain in too little/much detail. By having such a structured index of knowledge the model would be much better at the specific needs for that student. The main issue was ingesting these textbooks and its associated licensing/IP rights. I even made a request to BBC for use of their open source Bitesize content. But honestly AI firms just scrape everything, and I don't think I could have been sued anyways since I was using it for non-commercial purposes. 

Overall it was a great experience, and I definitely feel taking it beyond the hackathon was a great step. Who knows where my next hackathon will take me?