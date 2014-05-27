---
layout: post
title:  Two share links about (multi-armed) bandit algorithm
description: online learning
category: blog
---
<h2>{{ page.title }}</h2>
<p>what's (multi-arm) bandit algorithm ?</p>
<div>
  <span>
    epsilon-greedy algorithm
    <br />
    <br />
    With probability 1 – epsilon, the epsilon-Greedy algorithm exploits the best
    known option.
    <br />
    • With probability epsilon / 2, the epsilon-Greedy algorithm explores the best
    known option.
    <br />
    • With probability epsilon / 2, the epsilon-Greedy algorithm explores the worst
    known option.
    <br />

    <span><p>one arm denotes one option</p></span>

    when pulled, any given arm will output a reward.
    <br />
    you need to cope with risk by figuring out which arm has the highest average reward.
    <br />
    what makes a bandit problem special is that we only receive a small amount of the information about the rewards from each arm.
    <br />

    we only find out about the reward that was given out by the arm we actually pulled.
    <br />
    whichever arm we pull, we miss out on information about hte other arms that we didn't pull.
    <br />


    every time we experiment with an arm that isn't the best arm, we lose reawrd because we could, at least in principle, have pulled on a better arm.
    <br />

    </span>
    <br />
    <span style="color:green;"><b>Here are two links about multi-bandit algorithm that may help you</b></span>
    <br />
</div>
<a href="http://pdf.th7.cn/down/files/1312/bandit_algorithms_for_website_optimization.pdf">Bndit algorithm for website optimization</a>
<br />
<a href="http://www.cs.mcgill.ca/~vkules/bandits.pdf">Algorithms for the multi-armed bandit problem</a>
<p>{{ page.date | date_to_string }}</p>
