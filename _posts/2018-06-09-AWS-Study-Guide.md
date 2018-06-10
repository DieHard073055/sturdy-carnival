---
  layout: post
  title: AWS Study Guide
  subtitle: A general guide on how to study for aws certification exams
  tags: [ certification, examguide, aws, study ]
  categories: Exam Study Guide
  author: Eshan Shafeeq
  header_img: 
---

# Learning

### Distributed Practice
Spend a little bit of time every day of the month. Spreading out the learning makes things stick. 

### Varied / Interleaved Practise
Frequently change tasks and topics so that you are forced to think about the material in different ways. Easier to learn new things by incoperating and reinforcing previously-learned material. Let your existing **mental model** help you learn new things. Use your mental model often since it will help you strengthen and refine it. 

### Spaced Repetition
Review Information before you forget it completely. Revisit information when your mental model has improved. Spread out the learning time. 


# Zooming in & Zooming out

> Wikipedia : [A]bstraction is a technique for arranging complexity of computer systems. It works by establishing a level of complexity on which a person interacts with the system, suppressing the more complex details below the current level.

**Abstractions** are very important in software systems. It is the foundation of amazon web services. (*but just really anything in technology is*).


* Your goal is to architect and build systems. Think about the data flow through your entire system. 
* Nothing exists in isolation, services interconnect, the systems interacts with other systems. 
* Change over time is a key dimension in all tradeoff decisions, a "perfect" system that cannot be changed is fundementally broken, because the context around that system will eventually change.
* Technically debt, what you do now determines how easy it will be to make changes later. 

# Mental Models

**You remember things you understand**

> The image of the world around us, which we carry in our head, is just a model. Nobody in his head imagines all the world, government or country. He has only selected concepts, and relationships between them, and uses those to represent the real system. 

### What is a mental model
* A simplified representation of reality that your mind uses to anticipate events or draw conclusions. A way to describe what your brain builds when you understand something. The way your brain organizes information it learns into heirarchies, its when you use logic instead of memorization. Recognizing patterns.

### Value Proposition
* Predictive capability
* Quicker and easier learning: Understanding vs Memorization.
* Brain is better at remembering related concepts than unrelated details.
* More memorization can dilute older information.
* More understanding improves mental models.

### How to build a mental model
**Double loop learning**

##### Single loop learning
Is error correction by following the rules and operating norms when solving problem. Some thing like a feedback control loop. 

##### Double loop learning
Is error correction by changing and critically questioning the rules and operating norms when solving problems.

* This involves more thinking outside the box.
* Creativity is a must.
* Thinking outside the operating norms.

This allows us to question which situation is the best to reach our end goal.


### Progression ( Building the mental model )
* When new information clashes with your mental model, you will have to rebuild your mental model. **Forced rebuilds**
* Eventually becomes more robust and require fewer major changes, which results for efficient assimilation of info, high-efficiency learning and functional expertise.

# Questions

* Elaborative investigation uses questions like "why?" and "how?" to understand the meaning of information to be learned.
* Socratic Method, based on asking and answering questions to stimulate critical thinking and to draw out ideas and underlying presumptions.
* Five whys - used to learn the root cause of a defect or problem by repeating the question "why?". Each answer forms the basis of the next question.

### Why?
* Keep asking this about everything.
* Why does this service or feature exist? why would someone want it?
* Why does it work the way it does?
* Why are the limits set the way they are?

* Are they for my protection?
* Are they to help AWS manage scaling?
* Are they trying to encourage/force me to use better designs?
* Are they implementation artifacts?

### What?
* What assumptions have i made?
* What assumptions have aws made?
* What is the key purpose of this service/feature?

### When?
* When does the abstractions leak? When does what i know ( believe ) change?
    * Does it break under load?
    * During certain kinds of outages? ( AZ down? Other service having problems? )
    * Randomly but rare? ( Amortized costs? Network glitches? )
* When might i get throttled or hit service limits?
    * Which ones are fixed in stone?
    * Which ones can be changed?

### How ?
* How is this similar to what i've seen before?
* How is this different from what i've seen before?
* How did they build this?
    * Based on my understanding, what should be the limitations?
    * Am i right about this?
* How can i test what i believe?
* How does AWS handle failures?
* How do i handle failures?
* How does this intergrate with other services?


### Who ?
* Who is the target for this service?
* Service offerings target real user scenarios - based on customer feedback
* Integrate those into your mental model to make better predictions about how it should / does work.

# How teaching others can help

### Teaching
Forces you to communicate what you have learned. Requires you to understand the material more deeply. May also result in further questions that you hadnt considered. Explaining in detail to someone else will concrete these in your head.

### Dive in!
* Find a forum question that interests you. Research it until you can answer it. With full explanations. Make your response defensible, not just an opinion or guess. Use quotes from and links to official documentation!

### 30 Second Summary
* On any topic or technology.
* Recite a 15 to 30 second summary.
* Key strengths.
* Key weaknesses.
* How it interacts with other services.

# Visualization

Its not just vision.
> The words "visualization" and "imagery" are in some ways misleading. while the domiant sense is usually vision, visualization does not just involve seeing. The more senses you involve, the stronger the effect. Hear a switch click when you turn it on, or feel an engine turn over and the vibrations when you start it. Smell fuel when you check a fuel tank.. All these can significantly improve how your visualizations work.

### Example
* Imagine yourself as a network packet.
* On your way home ( a client system ).
* To work ( a load-balanced server in a VPC ).
* Driving and turning along roads ( network hops, routing, load balancing ).
* And passing security checkpoints (firewalls, network ACLs, security groups).
* Some are machines that always check your papers ( stateless; nACLs)
* Others have guards that remember you on the way back ( stateful;SGs )

# PDCA

### What is PDCA
* Plan
    * Plan what youre going to do to learn some new material
* Do
    * Do what you planned; set about actually learning it.
* Check
    * Check how well that plan worked-both how easy and how effective it was.
* Adjust
    * Adjust your plan for future learning, emphasizing techniques that worked well.


# What to do before the exam

### Month before
* Read AWS Certification FAQ
    * Think about the exam process.
* Read Exam blueprint
    * Pay attention to the exam waiting in each content domain
    * Read every line item.
* Take ACLOUD.Guru certification course final practice exam
    * Take for first time, as assessment.
    * Repeat until consistently scoring 100%.
    * Understand why every incorrect answer is wrong.
    * Unserstand why every correct answer is right.
* Read certification course forum posts about the exam feedback.
    * Read throught the 20-30 highest-ranked from the last 2-8 weeks.
    * Read through all exam related posts from the last 2-8 weeks.

### Week or Two Before
* Take aws practise exam for the first time.
    * Late enough to evaluate yourself.
    * Early enough to refresh on weak areas.
    * Early enough to reschedule / cancel without penalty, if necessary.
    * Take screenshots!
    * Rip the questions and responses apart!
* Read the latest exam feedback forum posts.
* Schedule exam.


### Day Before
* Rewatch training course summary lessons
* Review your own notes.
* Download some key course videos to phone.
* Read top forum posts with details to remember.
* Consider reading most recent forum posts for very latest feedback.
* Read AWS sample questions.
* Review questions from AWS practise exam.
* Review memorization items.

### Evening Before
* Double check details.
    * Exam location
    * Exam time.
    * All Documents ( Govt-issued picture ID ) ( Additional ID ).
    * Set out printed exam details.
* Metally prepare.

### Just Before
* Come early!
    * Last minute review notes
    * watch key downloaded training videos
* Go to the bath room.
* Validate IDs and the exam registration with proctor
* Lock up everything you have.
    * Empty every pocket of everything.

