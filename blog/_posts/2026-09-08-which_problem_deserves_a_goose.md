---
layout: post
title: Which problem deserves a goose?
description: >
  The AI scientist, and what is left for theoretical physicists.
sitemap: false
---

<!-- 2026-09-08 -->

<!-- related_posts:
  - /blog/_posts/2025-01-07-symmetries_neural_quantum.md -->

<!-- image: /assets/img/blog/blogpost_ai_scientist_cafe_loop.svg -->

***

In 1936 mathematician Stanisław Mazur wrote Problem 153 into a notebook kept by the waiters of the Scottish Café in Lwów. The café was the working room of what is now called the Lwów school of mathematics: Banach, Mazur, Ulam and a few other Polish mathematicians, who spent their afternoons and evenings there and, between them, invented much of functional analysis. When a problem survived enough discussion, it went into the notebook, with a prize attached: a small beer, a bottle of wine. For 153, Mazur offered a **live goose**. The prize was, in effect, a guess at difficulty: beers for an evening's work, a bottle for a hard one, a goose for a problem Mazur did not expect to see solved in his lifetime.

<p style="text-align:center;"><img src="/assets/img/blog/blogpost_ai_scientist_scottish_cafe.jpg" width="380" loading="lazy"/></p>
Fig. 1: The Scottish Café in Lwów, 1930s.
{:.figcaption}

The notebook outlived the café, and it outlived many of the people who wrote in it. After the war a copy reached Ulam at Los Alamos, and he translated it himself and sent copies to anyone who asked. Thirty-six years after Mazur wrote his problem down, a young Swede solved it and came to Warsaw to collect his goose.

What strikes me about that story is not the goose. It's that a school working out of a café, with almost no money, far from the great centres of mathematics, built one of the great bodies of twentieth-century mathematics with, at its centre, a book that recorded not their theorems but their questions. They had a journal for theorems, like everyone else. The Book was a second publication system, kept where anyone at the table could open it.

Strip away the coffee and the goose, and the café ran a simple loop: someone chose a question worth writing in the Book, someone came back the next morning with an attempt, someone else checked it. That loop is what the **AI scientist** is trying to automate — and the question I'll keep returning to is which of the three steps it gets to last.

Here, by an **AI scientist** I mean systems built on **large language models** (LLMs) that read the literature, propose a hypothesis, run the calculation or simulation, check the result and write it up, with humans in the loop needed less and less. How good are these AI scientists already, and where are they heading? A lot of people have been asking me lately, so here is my attempt at an answer, in two parts. First, a critical look at where the AI scientist actually stands, and why I expect it to keep improving. Then some bold projections, and the questions about physics, physicists, and physics education that I think follow from them. We will revisit the Lwów café and its Polish mathematicians along the way.

**Disclaimer:** This is a rapidly moving field, and I have hesitated to write publicly about it for a while; what follows is therefore best read as a collection of my subjective judgements and only as a snapshot of my current understanding. I write from theoretical physics; experiment is a different story, and I only gesture at it below.

* table of contents
{:toc}

## What is the current state of affairs in agentic science?

Let’s start from **science benchmarks.** For a while LLM progress for science was measured on benchmarks such as [GPQA-Diamond](https://epoch.ai/benchmarks/gpqa-diamond) – a set of graduate level exam-like, multiple-choice questions from physics, biology and chemistry. These benchmarks have been pretty much saturated.

There are now benchmarks that are much closer to real scientific work than the usual exam questions. **Terminal-Bench-Science**, for example, asks agents to complete 70 expert-designed research workflows involving simulation, data analysis, proofs, optimization and other scientific tasks; there has been a rapid progress on this benchmark: at its launch earlier this year the best agent (Claude Opus 5 with Claude Code) solved 30% of the tasks, with the next ones at around 20%; by September the labs were reporting 52.6% for Claude Fable 5.1 and 64.6% for GPT-6 Astra \[[leaderboard](https://www.terminal-bench-science.ai/announcement), [OpenAI announcement](https://openai.com/index/gpt-6-astra/)\].

For physics specifically, **CritPt** is quite interesting. It contains 71 research-level physics challenges written by active researchers, spanning condensed matter, quantum information, AMO, high-energy physics, astrophysics and others; the problems are designed to resemble junior-PhD-level research tasks rather than textbook exercises. Current frontier models remain far from solving these reliably: the original evaluation found about 4% for base models and about 10% with coding tools, with current best scores (GPT-5.6 Sol and GPT-6 Astra) in the low 30s \[[leaderboard](https://artificialanalysis.ai/evaluations/critpt)\]. In the Lwów café's terms: the exam benchmarks were beer problems and are gone; CritPt is a bottle of wine, and the models are about a third of the way through it; the goose problems are not on any leaderboard yet.

There is also a growing field of **autonomous research.** One of the first such end-to-end systems came from machine learning research itself: **Sakana AI's AI Scientist** ([*Nature*](https://www.nature.com/articles/d41586-026-00899-w)[ 2026](https://www.nature.com/articles/d41586-026-00899-w)). Its agentic workflow generates ML research hypotheses, runs experiments, analyzes the results and writes a paper — end-to-end without human intervention; one of three generated submissions by this system was accepted at an ICLR 2025 workshop. Another interesting direction is search rather than autonomy: Google DeepMind's **AlphaEvolve** ([2025](https://arxiv.org/abs/2506.13131)) evolves code against an automatic evaluator and has produced new algorithms, records in combinatorics and, more recently, lower-error quantum circuits for Google's Willow processor; **ERA** by Google Research ([*Nature*](https://www.nature.com/articles/s41586-026-10658-6)[ 2026](https://www.nature.com/articles/s41586-026-10658-6)) combines an LLM with tree search over code to write scientific software, and beat the human state of the art on single-cell analysis and COVID forecasting.

<p style="text-align:center;"><img src="/assets/img/blog/blogpost_ai_scientist_alphaevolve.png" width="800" loading="lazy"/></p>
Fig. 2: AlphaEvolve workflow \[from the [original paper](https://arxiv.org/pdf/2506.13131)\].
{:.figcaption}

In physics, already in 2024 Pan, Tikhanovskaya and collaborators ([*Comm. Phys.*](https://www.nature.com/articles/s42005-025-01956-y)[ 2025](https://www.nature.com/articles/s42005-025-01956-y)) showed that GPT-4, given carefully templated prompts, could reproduce the Hartree-Fock derivations of 13 out of 15 recent condensed-matter papers; more recently Nägele and Marquardt's **SciExplorer** ([*PRX*](https://journals.aps.org/prx/abstract/10.1103/xnqc-q6nt)[ 2026](https://journals.aps.org/prx/abstract/10.1103/xnqc-q6nt)) lets an LLM agent run its own numerical experiments on a system it has never seen and recover its equations of motion or Hamiltonian, with no task-specific instructions. There are also smaller, closely supervised attempts at real research. Matthew Schwartz at Harvard [coached Claude](https://www.anthropic.com/research/vibe-physics) through a full particle-physics calculation using text prompts only, and got a publishable paper with a new result in two weeks instead of a year — while having to catch the model faking its own checks along the way. And a Harvard–OpenAI collaboration around Andrew Strominger, having found a new formula for how gluons scatter with the same model's help, [handed the paper to GPT-5.2 Pro](https://openai.com/index/extending-single-minus-amplitudes-to-gravitons/) and asked it to do the same for gravitons; it did, by a route the authors had not expected, and the humans report having verified every step.

So the baseline is uneven in a specific way. Reproduction of a known derivation, given some structure, is essentially solved. Extension of a known result works when a human supplies the target and re-verifies every step, as in the Schwartz and Strominger cases. Open-ended research is largely untouched: in a recent [shadow evaluation](https://arxiv.org/abs/2607.27191), frontier agents given the open question of an unpublished NeurIPS paper, six days and thousands of dollars of compute completed all the engineering and still made no real progress on the question.

One caveat: much of the progress inside AI-scientist companies (Periodic Labs, CuspAI, Lila Sciences and others) is unpublished, so the real state of the art is ahead of the public one; see for instance [this talk](https://www.youtube.com/watch?v=Oru2Jxr1xHU) by Liam Fedus of Periodic Labs.

What should strike us, though, is less the current status than the speed of progress. This naturally prompts us to ask the next question.

## Why should we expect the AI scientist to improve further?

<details class="learning-box">
<summary><b>VOCAB BOX:</b> Let’s start from a quick recap of the vocabulary to set the stage. </summary>
<div markdown="1">

- LLMs are models which consume textual input which is turned into a set of “tokens” (which loosely map to chunks of text, typically a word or a piece of one) and then processed by a (transformer-backbone) neural network with certain **weights** which ultimately determine the set of output tokens \[further dividing for reasoning LLMs into “reasoning” tokens and “visible output” tokens\].
- Now weights for models such as GPT-6 or Claude Fable are **closed** \[i.e. public does not know what they are\] vs for some others — such as Kimi K3 or GLM 5.3 — they are publicly available i.e. models are **“open-weight”**.
- Weights of an LLM are trained during pre-training of the model and can be further modified with reinforcement learning (RL) during post-training or fine-tuning stages.
- The max length of the input visible to the LLM is known as “context window” which for most 2026 models is around 1M tokens.
- LLMs can be further equipped with access to tools (such as running commands in terminal, reading files etc.), context management mechanisms (e.g., compactification) and then they are known as “**AI agents**”.
- Further scaffolding around agents orchestration and curated context loading (”skills”, “AGENTS.md”, memories etc) is often referred to as **agentic harness.** What I refer to as **“AI scientist”** here is a form of an agentic harness for more or less specialized science tasks.

</div>
</details>

Having set the basics, there are a few stages of how one improves LLMs. They can be roughly divided into improvements during **pre-training, post-training and agentic harness.** When the last two keep happening during deployment, from the agent's own experience, this is called [continual learning](https://www.lesswrong.com/posts/5mCJzimtNZc9o4e26/what-s-continual-learning-and-why-might-we-expect-to-see-it).

First, there is **pre-training:** teaching LLMs how to predict next token better. Scaling models \[see [neural scaling laws](https://arxiv.org/abs/2001.08361)\], improving data quality and incorporating more scientific material continue to improve the raw substrate on which these systems operate; relatedly progress on developing **longer usable context windows** will also allow an agent to keep much larger parts of a calculation, codebase or literature trail in view.

Second, **post-training** is itself becoming a major scaling axis. Within this phase of the training the goal is to maximize the LLM’s performance on a given set of reasonably general *verifiable* tasks e.g., LLMs generate reasoning traces which attempt solving math problems; such traces are graded, and based on that feedback the model weights are modified through RL training.

More RL compute and better verifiers can turn the same base model into a substantially better problem solver; there may not be one clean “scaling law” here, but empirically there is still a lot of room to spend computation more intelligently after pre-training.

<p style="text-align:center;"><img src="/assets/img/blog/blogpost_ai_scientist_cafe_loop.svg" width="680" loading="lazy"/></p>
Fig. 3: The café loop as of September 2026. Shaded steps are the ones the machine now does; the dashed one is still Mazur's.
{:.figcaption}

This also explains the order in which the café loop gets automated. Recall its three steps: choose a question, attempt it, check the attempt. Checking a proposed solution has a grader by construction — the check *is* the grader. Attempting a solution to a given problem has a grader whenever the answer can be verified, which is true of nearly everything on the benchmarks above. But choosing which problem to attempt in the first place — was this a good question to ask? — has no grader on any short horizon; today you find out years later, if at all, because attempts are expensive and few. It is also because the point of theory is for humans to understand the world, so "interesting" means interesting to us — which no swarm can measure, and which, less charitably, is also how fields end up trend-chasing. RL improves what it can grade, so it reaches the choosing step last. I don't think this is a fundamental bottleneck though: once attempts are cheap, one can imagine grading a question by what a swarm of agents makes of it a week later, and once enough such attempts exist that signal becomes cheap — though it rewards questions that yield quickly, which is not the same as questions that deserve a goose. And wherever a grader does exist, with **open-weight models** one can consolidate experience from solving a specialized set of *verifiable* tasks of interest back into the weights through fine-tuning, RL or mid-training.

Third come the **agentic harnesses**. Generic agents can already browse literature, write and run code, manipulate files and maintain notes; specialized scientific agents can additionally call symbolic-algebra systems, simulators, theorem provers, numerical solvers and experiment-specific verification tools. We have barely scratched the surface there, and I suspect properly engineered harnesses already allow for some limited form of self-improving systems. Maintaining robust **agentic memory storage** is a part of this. Instead of requiring everything to remain in the context window, agents can maintain structured notebooks, databases of past attempts, summaries and generalizable skills. Claude already has “auto-memory” and “[dreaming](https://platform.claude.com/docs/en/managed-agents/dreams)” features for this purpose. Although its current performance on generalization from past experiences is quite lacking I anticipate this will be a pretty major growth pathway.

Another important axis of progress within umbrella of improving harnesses is **agentic orchestration** i.e. how agents interact with other agents. People have experimented with generator–reviewer systems (bear in mind though that the evidence on their usefulness is somewhat mixed: Google's [AI co-scientist](https://arxiv.org/abs/2502.18864) reports gains from a generate–debate–evolve loop, while a recent [ICML 2026 workshop paper](https://openreview.net/pdf?id=RyX98G24rP) finds the opposite), with delegating to subagents to keep context small (see [Anthropic's write-up](https://claude.com/blog/building-multi-agent-systems-when-and-how-to-use-them)), and with models fine-tuned for a speciality. For instance, a scientist-agent can have separate planners, critics, numerical checkers and independent solvers attacking the same problem, which begins to look less like “one chatbot thinking very hard” and more like a small computational research group.

Taken together, there is simply **a vast and mostly unexplored design space**. It would be surprising if today's systems were anywhere close to the best possible combination. A lot will change in how we do physics. Before going on, let me deal with some objections I hear repeatedly.

### Some common misconceptions FAQ

**“But LLMs don't really have *real* memory.”** Not in the human autobiographical sense, perhaps, but this matters less than it sounds: persistent external memory, searchable research logs and explicit knowledge stores already exist, and model weights themselves can also be updated. The engineering question is whether useful information survives and can be retrieved at the right moment.

**“But LLMs don't really reason.”** There is an interesting philosophical and mechanistic question here, but for forecasting scientific automation it is almost secondary. If a system can repeatedly construct a correct derivation, notice contradictions, test alternatives and recover from errors, arguing over whether this deserves the word *reasoning* does not change its usefulness for science.

**“But everything an LLM produces still has to be checked by a human.”** Sometimes—but an increasing fraction of scientific work admits automated checks: compiling code, reproducing a figure, numerically evaluating a formula, checking a proof, comparing a simulation against known limits, or running a battery of unit tests. Having said this, as I’ve mentioned before problems which are hard for LLMs are often ones for which we do not possess good graders, so skepticism remains necessary.

**“But LLMs don't understand the physical world.”** I think there is something important hiding in this objection, especially once we leave mathematics and simulation and ask about choosing useful abstractions for say experimental physics reality. This is a much broader question though and I think it deserves its own blogpost.

Do you see any visible bottlenecks for your field? I’d be curious to know.

Ok, now, with the objections out of the way, what does all this do to physicists?

## Implications for physics

### Emotional responses to AI progress

I see two almost opposite reactions. I will call them “East Coast” and “West Coast,” although these are caricatures of intellectual temperaments rather than literal geography.

The **East Coast reaction** is often hesitation. A scientist has spent ten or twenty years becoming able to perform some difficult intellectual operation and naturally views that ability as part of their identity; they are happy to delegate literature formatting or routine coding to an LLM, but much less comfortable testing whether it can touch the thing they regard as their actual intellectual contribution.

The **West Coast reaction** has the opposite failure mode: excessive enthusiasm from people who do not always appreciate what scientific discovery consists of. Suppose a system hands you a correct 200-page Lean proof of an open conjecture. Is that progress? Thurston argued long before LLMs ([1994](https://www.math.toronto.edu/mccann/199/thurston.pdf)) that progress in mathematics is advancing *human understanding*, and a proof is only one vehicle for it; part of what makes a question interesting is that answering it forces a new language — new definitions, new objects, new relations between them. His own example was the four-colour theorem: everyone can explain how the proof works — check every case — and no one would say that tells you *why* it is true. Gowers makes the same point about the [AI disproof of the unit-distance conjecture](https://cdn.openai.com/pdf/74c24085-19b0-4534-9c90-465b8e29ad73/unit-distance-remarks.pdf): the ingredients were already in the literature, so the result settles the question without changing how anyone thinks. So far this is where the systems stop, and the reason is the one from the post-training section: there are two kinds of answer, and only one has a grader. Correctness is checkable; whether a proof gives us new language is not — at least nobody has yet worked out how to grade it. The same gap that delays the choice of question also delays this kind of answer, and the prediction is the same: the checkable kind arrives first.

Somewhere between these two reactions there is often some form of an **existential crisis**. If an ability on which you built much of your professional identity suddenly becomes cheap, you have to ask what part of your work you actually care about. It is not necessarily a bad thing: I have seen multiple people now who have responded to such a crisis in very productive ways.

This raises a broader question: what does this do to physics education?

### Effects on theoretical-physics education

The effects will cut both ways.

One immediate danger is a modern version of what Feynman called **“computer disease”**: becoming fascinated with everything the machine lets you do rather than asking whether any of it matters. Feynman's original complaint was about the delight of making computers perform elaborate but useless calculations; LLMs dramatically amplify the same temptation because generating another calculation, conjecture or polished document is now almost free. We should therefore expect enormous quantities of plausible-looking garbage. Producing articulate scientific “bullshit” \[in a Frankfurtian sense: see [this paper](https://link.springer.com/article/10.1007/s10676-024-09775-5)\] used to require substantial effort; now the prose, equations and figures can all look respectable while the underlying idea remains confused or half-baked.

A deeper problem is motivation. If a student believes a machine can derive in thirty seconds what would take them an afternoon, many will simply stop wanting to follow the derivation \[or even better — do it themselves\] or study toy models.

Now, on a positive note, a small fraction of students may become enormously more powerful. When stuck in a calculation, for example, they can ask: *Is my physical picture wrong, am I missing a theorem, or have I merely made an algebra mistake?* Rapid feedback of this kind can make deliberate learning much faster rather than replacing it.

The resulting distribution may therefore become wider: fewer people develop deep independent understanding, while a small group who insist on understanding things become dramatically more capable.

### How should a (young?) physicist respond?

I don’t have good answers. Here are some partial ones. First: still study **toy models** aggressively. If you can strip a phenomenon down until you genuinely understand every moving part, you are much less likely to become someone who merely supervises plausible-looking machine output.

Second, become even more intellectually flexible. LLMs make it much cheaper to cross disciplinary boundaries: you can obtain a first working understanding of an unfamiliar field, its notation and its central papers in hours rather than days.

Third, use agents to test ideas quickly, but do not confuse testing with understanding. The fastest workflow I have found is to communicate at high bandwidth: short statements of the problem, explicit assumptions, small executable tests, concise summaries and visualizations that allow you to see immediately whether the agent and you are thinking about the same object.

Finally, move upward in the stack—but not into empty abstraction. Questions about which phenomena matter, which approximations reveal something fundamental, which measurement would distinguish two pictures, or where a theoretical idea could touch the physical world may remain more valuable than producing the hundredth variation of an already well-specified calculation.

### Will we still need theoretical physicists?

Probably—but perhaps not in the same way we need them today. Let me explain.

#### Some uncomfortable possibilities

One possibility is that parts of science become more directly **proportional to money**. This is not completely new: experimental particle physics or astronomy have long depended on extremely expensive infrastructure. What may be new is that even comparatively “cheap” theoretical research could acquire a meaningful capital component if access to the best models, inference compute and agent ecosystems gives researchers a large productivity advantage. This could create a strange **scientific inequality**. The relevant question would no longer only be whether you are clever enough to attack a problem, but whether your lab can afford to run thousands or millions of serious attempts on it.

The Lwów café is the obvious objection: great mathematics for the price of coffee. But theory in physics has been split in two for a long time. The numerical half has tracked the biggest computer available since Ulam's generation left the café for Los Alamos, and much of it is already proportional to money. The pen-and-paper half, the derivation, the model, the choice of approximation, still ran on the café budget. The AI scientist puts a price on that half too. Maybe that price collapses, the way a 1950s supercomputer calculation now runs on a tiny laptop. But something else changes: the boundary. Any theoretical problem with a checkable answer — a derivation that can be evaluated numerically, a limit that can be compared, a proof that can be verified — now sits on the compute-priced side of the line, and more compute buys more attempts. That is how the checkable half of theory becomes proportional to money. The returns are not unlimited: doubling the attempts does not double the successes, and without a verifier extra attempts buy little. But that caveat cuts the other way: the problems that stay cheap are precisely the ones we can't grade, which are also the ones a café can still do. So the line that splits theory is no longer numerical versus pen-and-paper, but gradable versus not.

Our **publication and peer-review system could also become increasingly bizarre**. If generating and checking candidate answers becomes cheap, then *posing the right question* becomes relatively more valuable; a beautifully formulated problem may contain more scientific insight than the machine-generated solution that follows.

That raises awkward questions about priority and secrecy. If revealing a question allows someone with greater compute to solve it immediately, researchers may become more cryptic about unfinished ideas—the opposite of what an open scientific culture should want. Robert Huang makes related points for quantum information in [this talk](https://simons.berkeley.edu/news/how-respond-automation-research).

Mazur wrote Problem 153 into the Book, and attached a goose to it, precisely because he expected it to be hard and wanted others to try. The Book worked because the gap between writing a question down and seeing it solved was long — decades, for Problem 153. That gap is what gave Mazur credit for asking and everyone else a fair chance to try. The AI scientist collapses the gap. If a well-posed question can be resolved in a day by whoever has the most compute, and if our credit conventions keep rewarding the solver over the poser, the incentive flips: you keep your goose problems to yourself. The second "if" is the one worth fighting over.

There is also a more philosophical possibility: perhaps AI eventually produces science that humans cannot really understand. A mild version already exists — AlphaEvolve's constructions, the four-colour and Kepler proofs: verified, used, and not understood in the sense a physicist means. But in each case the verification was the deliverable and nobody was asked for the understanding. Explaining a result to a human is itself a task with a grader — does the reader, afterwards, reproduce the argument unaided? — which puts it on the side of the line these systems are good at. So I expect explanation to be cheaper than discovery whenever anyone wants it. The exception is the paradigm-shifting kind of discovery, in Kuhn's sense, which by definition only makes sense once you change the framework you think in. There the bottleneck is not the explanation but how fast we can learn new concepts.

#### The good side

The obvious upside is **parallelization**. Instead of a physicist testing three variants of an idea in a week, a research system might test three thousand, while many such systems work simultaneously on different parts of the scientific landscape.

Scientific publication itself may become richer, and here the Lwów café offers a hopeful precedent: a second publication system — just for questions — next to the journals, for things journals do not carry. The [**Agentic Publication Protocol**](https://arxiv.org/abs/2606.27386), for example, proposes publishing not just a static PDF but agent-readable metadata, code, environments and instructions that let future agents reproduce and extend a result directly. Related projects such as [**Agent-Native Research Artifacts (ARA)**](https://arxiv.org/abs/2604.24658) go further and treat failed attempts, experiment trajectories and verification records as first-class scientific outputs. This makes sense in an agentic world: if another researcher can inherit not only your successful result but also the hundred things you already tried and disproved, scientific knowledge compounds much faster.

Agents may also become extremely good at scientific **due diligence**. Humans are bad at consistently running boring checklists; machines can systematically test limiting cases, reproduce figures, rerun analyses under alternative assumptions and keep precise records of every step.

And that, ideally, lets humans spend more time on the part of physics that attracted many of us in the first place: trying to understand what (the hell) is going on.

## Conclusion

After all of this, it feels a little odd to admit that I am not sure "will AI replace physicists?" is even the right question. In the short term, agentic AI will more likely replace a growing list of the activities that currently occupy physicists, while making an unusually capable physicist far more productive. In the longer term, whether it replaces most of what we currently call theoretical physicists turns on the thing this essay has kept returning to: whether someone builds a grader for questions. If the choosing step stays ungraded, physicists keep the goose and the machine keeps Banach's mornings. If it doesn't, I don't see what else protects the job. At the risk of the West Coast failure mode I criticised above, I'll say what I actually believe: I think the grader gets built, and "longer term" is a few years rather than a few decades. Here is how to check me. Watch the open-question evaluations. The day an agent makes real progress on an unpublished open problem — the problem, not its checkpoints — this prediction is on schedule. While they keep finishing the engineering and stalling on the question, it isn't. Note what that tests: whether the machine can win a goose someone else set — and not how to set one.

I want to end with four questions rather than more concrete predictions \[to avoid embarrassing myself a few years down the line!\].

The first is pragmatic: **if you are about to start an undergraduate degree or a PhD in physics, should you still do it when the scientific world may look radically different three to five years from now?** I will deliberately leave this unanswered; it is a profound question involving economics, identity, curiosity and risk tolerance, and deserves more than a paragraph.

The same problem exists in many knowledge professions, although interestingly it feels less acute if you are deciding whether to become a plumber. That contrast is a nice illustration of **Moravec's paradox**: some abstract intellectual tasks that humans experience as difficult can be easier to automate than the sensorimotor competence we normally take for granted.

The second question is more immediate: **are you at a university or workplace that will give you sufficient access to frontier AI?** This is subtly different from access to GPUs: the bottleneck may involve subscriptions, inference budgets, proprietary research systems and organizational willingness to let people use them, although how large this advantage remains will depend on how commoditized frontier models become.

The third is the deeper question: **why did you want to do physics in the first place?** If the answer was that you enjoyed being unusually good at solving hard calculations, the next decade may be uncomfortable. If the answer was that you wanted to understand the physical world, things may be about to become even more interesting.

And finally, one question for the field rather than the individual: **if choosing the question is the part that stays human, who gets to choose?** A system that answers any well-posed question at compute price will be pointed at whatever its owners find worth asking. That is not an argument for slowing down; it is an argument for being explicit about which problems deserve a goose — and for keeping the Book where anyone at the table can open it.

<p style="text-align:center;"><img src="/assets/img/blog/blogpost_ai_scientist_mazur_goose.jpg" width="300" loading="lazy"/></p>
Fig. 4: (1972) Mazur (left) handing “the young Swede” Per Enflo the live goose for solving Problem 153.
{:.figcaption}

Let me finish this story back in Lwów. Banach would turn up the morning after a café session with a proof on loose sheets, sometimes incomplete, sometimes wrong, and Mazur would put it right. That part of the job is what the machine now more or less offers to do for anyone who asks, and it will do it faster every year. What it does not yet offer is to tell you which problem *deserves a goose* — not because that judgment is sacred, but because it is the one step in the loop nobody has yet worked out how to grade.

**Acknowledgements:** I’d like to thank many of my colleagues, in particular Jack Kemp, Shashvat Shukla, Robert Adragna and Sajant Anand for providing feedback on the draft version of this blogpost.
{:.message}
