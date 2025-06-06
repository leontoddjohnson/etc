---
title: assignments
weight: 2
---

# assignments

I define an "assignment" as *anything a student is asked to submit in Canvas*. In my classes, this includes class activities, course projects, and weekly exercises, labs, and write-ups. Here, I'll discuss the following approaches I use for these assignments, along with some examples:

- Transparency in Learning and Teaching (TiLT)
- Peer instruction
- Project-based learning
- Using A.I.

*Note: the examples below should also illustrate how I keep assignments practical, and informed by work that students should expect to do in a job setting.*

## TiLT

Each of my assignments in Canvas use the [TiLT framework](https://www.tilthighered.com/about/about-tilt), in that each assignment is presented with

1. the purpose for the assignment,
2. the task, and
3. the criteria for success.

In practice though, 2 and 3 tend to be combined in the same section. That is, the "criteria" is *defined* by the "task", and *informed* by the EMRN rubric (see below). This sort of interpretation of TiLT is also reflected in [this example](https://bdl2jezatgadvbda.public.blob.vercel-storage.com/pdf/Example%20D-IQIjtxwpfvVQDdp7fTnm2vFwPEVHpm.pdf) of an assignment, gathered from the [TiLT resources page](https://www.tilthighered.com/resources).

### example: week 4 data dive

As an example, below is the Week 4 assignment for my statistics class. Each week, the statistics students are asked to investigate their data using what they learned that week — this is a "data dive". Below is the assignment for Week 4.

{{% details "Week 4 Data Dive" %}}

**Purpose:**

The purpose of this week's data dive is for you to think critically about what might go wrong when it comes time to make conclusions about your data.

**Task:**

Your RMarkdown notebook for this data dive should contain the following:

- A collection of 5 random samples of your data (with replacement). We are simulating the act of collecting data (like yours) from a population where the simulated "population" here is represented by the data set you already have.
  - Each subsample should be as long as roughly 50% percent of your data. 
  - Store each sample set in a separate data frame (e.g., df_2 might be the second of these samples).
  - Of course, these subsamples should each include both categorical and continuous (numeric) data.
- Scrutinize these subsamples. Note: you might find group_by quite helpful here!
  - How different are they?
  - What would you have called an anomaly in one sub-sample that you wouldn't in another?
  - Are there aspects of the data that are consistent among all sub-samples?
- Consider how this investigation affects how you might draw conclusions about the data in the future.
  - (optional) Try to incorporate Monte Carlo simulations here (see Lab 3) if you can.

For each of the above tasks, you must explain to the reader what insight was gathered, its significance, and any further questions you have which might need to be further investigated.

**Criteria:**

Refer to the EMRN Rubric. The above task dictates the "expectations".

{{% /details %}}

## peer instruction

In my statistics class, I've incorporated peer instruction (Mazur, 1997) into the class meeting using the [TopHat](https://tophat.com/) Canvas integration. After putting together several True/False questions, I would:

1. Present the question to the class, ask them to give their answer *individually*, and close their laptop.
2. They'll discuss with a pair partner what their answer was, and what their reasoning was.
3. I present the answer, and an explanation.
4. They discuss with their partner what they got wrong, or how they'd rephrase their reasoning.

Apparently students really enjoyed this method, as evidenced by positive feedback midterm self-reflections.

### example: practical mathematics

Each week, students in my mathematics course are assigned 8 True/False questions (on Canvas) in reference to a notebook like [this one](https://colab.research.google.com/drive/1D8YYES5Evd37m9DSz3Nsonmg0w7YmEEn?usp=sharing).[^fn:example_q] These questions are meant to apply what they learn from the (theoretical) lecture videos and slides seen before class meetings.

[^fn:example_q]: An example question could be *Refer to Situation 1. This matrix also represents an invertible linear transformation. That is, it does NOT "squash" a 4-dimensional vector into a 3-dimensional space.*

This creates a "gap between the theory and practice". To address this gap, I select a number of these quiz questions to work through *in class* each week using the peer instruction method, above. We would go through these after an in-class review of the lecture slides.

## project-based learning

In my data science programming course, I divide the class into groups of 3-4 students, and assign them a semester-long project. The idea is for them to build a [Streamlit](https://streamlit.io/) web app using several aspects of a typical development pipeline:

- GitHub version tracking
  - pushing and pulling
  - branching
- standup meetings (a la agile project management)
- environments (using pip)
- environment variables (with *.env* files)
- an introduction to the idea of Docker

Students will choose their own dataset (based on shared interest), and they meet each week to talk about their contribution to the project. They use what we learn in class to improve on their project, and (at least) the second half of every class period is devoted to project work with their group. I use [GitHub Classrooms](https://classroom.github.com/videos) for students to practice their Python skills on weekly exercises, and apply what they've learned to their project.

In my experience, students tend to be excited about using what they learn in a true "on-the-job" context, and working with data they enjoy keeps them engaged.

### example: standup report

As an example of how industry standards (e.g., agile project management) can be integrated into the project-based learning environment, here is what students in the above class are expected to do for their weekly standup reports:

{{% details "Standup Report" %}}

**Discussion Reply #1** (*before* lecture)

In a discussion post, please provide your group with a short report of your progress, including **all** of the following:

1. A detailed description of what you completed since last week.
   - Cross check this with your plan from last week ...
   - **You must include at least one screenshot image (e.g., a visualization, code output, etc.)**
2. List any roadblocks or issues you are having.
   - Try to be as explicit as you can here ... others in your group might be able to help!
   - If you can't think of anything, list what you are *currently* working on.
3. Explain what you plan to complete next week.
   - This should be reasonable — you can talk to others in your group for guidance if you like.

**Discussion Reply #2** (*during* lab)

**At the beginning of every lab session, you must verbalize your standup report to your group**. Explain each of your three points above, and take questions if your group has them. After everyone in your group has spoken, you'll need to **make a second reply** to this discussion with the following two items:

1. Give *your* evaluation of the group's progress. What has your group done *as a whole* so far?
2. Explain how *your* work this week affects (or is affected by) the work of someone *else* in your group.

**Both Part 1 and Part 2 are required for a "complete" score.** Part 2 is due at the end of class.

Keep in mind, the instructor or a TA may reach out to you separately to discuss your progress one-on-one.

{{% /details %}}

## using ai

*First, I should mention that there is a difference between the term Artificial Intelligence (AI) as I believe it to be [defined](/posts/20201212), and the term "AI" as it's colloquially used, namely, to refer to large language models (LLMs) like ChatGPT, and other similar products. For the purposes of this section, though, "AI" will refer to the latter.*

Recent developments in AI such as ChatGPT present an interesting opportunity for curriculum development in higher ed. In particular, Dr. José Bowen presents [several prompts](https://teachingnaked.com/complete-prompts-from-teaching-with-ai/) that could be used in building AI-driven assignments.

In the future, I'd like to incorporate more examples of the following kind of assignment:

1. Use AI to `<do something>`.
2. Share your prompt and what model you used.
3. Improve on the result, explain what you improved, and why.

This sort of thing creates a "manager-assistant" relationship between the student and the AI that is likely to be mirrored in the workplace in the near future. Also, it *encourages* students to use the tools in an educationally healthy way.

# the EMRN rubric

Aside from class activities, all assignments are evaluated using the following EMRN rubric, which is my adaptation of [Dr. Robert Talbert's version](https://rtalbert.org/emrn/) of the [EMRF rubric](https://miss-serwy.weebly.com/uploads/1/2/1/6/12161802/emrf_rubric_1.pdf) by R. Stutzman and K. Race.

<p align="center">
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTDNNNryzNZi1-VI_pRqLDla_T1X78lhcRKXqb85MEmYaV-XRdGPuJWRNsECi5ZVfxMFRV1JdJtzUA_/embed?start=false&loop=false&delayms=3000" frameborder="0" width="100%" height="400" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true">
</iframe>
</p>

One of the main changes I made here was to the definition of "E". Instead of "Exemplary" or "Excellent", I believe "Exceeds Expectations" to be a bit more explicit. That is, we have expectations defined in the criteria/task of each assignment. If a submission goes above and beyond those expectations, showing a clear indication of individualized and *volunteered* creativity, then it "exceeds expectations", and is marked with an "E".

# references

Mazur, E. (1997). Peer instruction: A user’s manual. Prentice Hall.

Stutzman, R. Y., & Race, K. H. (2004). *EMRF: Everyday Rubric Grading.* The Mathematics Teacher, 97(1), 34–39. https://doi.org/10.5951/MT.97.1.0034

Talbert, R. (2025). *The EMRN Rubric*. Robert Talbert, Ph.D. https://rtalbert.org/emrn/