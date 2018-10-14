---
layout: post
title: Identifying Security-Critical Components with Attack Path Planning
---

In my senior year at Carnegie Mellon University (CMU), I wrote a paper as part of a senior honors thesis about "Identifying Security-Critical Components with Attack Path Planning" with advisor David Brumley. 

[Full paper can be viewd here.]({{ '/public/img/posts/2016-05-31-attack-path-planning/thesis.pdf' | relative_url }})

## Abstract

The security of any system is only as strong as its weakest link.
Ideally, we would prefer to ensure that every component of a system
is secure. However, it is not feasible to put resources into inspecting
every component of a system as the cost to check for security vulnerabilities
does not scale well. The current approach to Identifying
Security-Critical Components is through attack path planning - finding
out how an attacker can violate the confidentiality, integrity or
availability of the system. An attack plan consists of a series of step
an attacker can take to compromise the system. These steps include
exploiting vulnerabilities in components of the system. However, we
do not know what vulnerabilities are present in the system. Our task
is to hypothesize (based on a potential attack plan) which vulnerabilities
are the most important to check for in a system (checklist items).
Our current system generates facts about the system using analysis
tools on system images, infers additional information from a set of
rules, and identifies attack plans via a simple backward search algorithm.

This thesis presents a new logic-based approach to tackling the
problem. We start with an introduction of the problem, and next
proceed to define our logic-based formulation of the problem based on
natural deduction and datalog. We then provide an overview of the
design, limitations and implementation of the system and test our new
approach against our previous system. In this thesis, we briefly discuss
our previous attempt at using Planning Domain Definition Language
(PDDL), another approach to the problem , and why it was not a
good fit.

Our new system reports a 2-3x speedup over the old system (at the
minimum search depth configuration for each test case). However, we
note that the system finds all possible attack goals, but not all possible
attack plans. We conclude that our current approach is promising in
scaling to multi-system attack plans and we explore future possibilities
that may eliminate existing limitations of the system
