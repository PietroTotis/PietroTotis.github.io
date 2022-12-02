---
# Documentation: https://wowchemy.com/docs/managing-content/

title: 'smProbLog: Stable Model Semantics in ProbLog and its Applications in Argumentation'
subtitle: ''
summary: ''
authors:
- Pietro Totis
- Angelika Kimmig
- Luc De Raedt
tags: [PLP, KRR, Argumentation, Journal]
categories: []
date: '2021-01-01'
lastmod: 2022-11-04T12:29:20+01:00
featured: true
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ''
  focal_point: ''
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
publishDate: '2022-11-04T11:29:20.115822Z'
publication_types:
- '2'
summary: "We model beliefs in argumentation problems with probabilistic logic programs and show that traditional probabilistic logic programming (PLP) systems cannot reason on this type of programs. We thus present smProblog, a novel PLP system based on ProbLog, where inference and learning over such probabilistic argumentation problems are possible."

abstract: 'We introduce SMProbLog, a probabilistic logic programming framework based on the probabilistic logic programming language ProbLog. Probabilistic logic programs are logic programs in which some of the facts are annotated
    with probabilities. The common assumption in probabilistic logic programming is that probabilistic facts fully capture the uncertainty in the domain under investigation. Probabilistic argumentation problems, however, represent an interesting practical application where this is not always the case. SMProbLog semantics supports probabilistic logic programs where a choice of probabilistic facts does not yield a unique interpretation of the logical atoms in the program. We implement the corresponding algorithms for both inference and learning tasks. The new semantics is essential to reason about epistemic probabilistic argumentation problems: we encode them as SMProbLog programs, and show how the implementation of SMProbLog can be used as a system for inference and learning over probabilistic argumentation problems. We evaluate our approach with experiments analyzing the computational cost of the proposed algorithms and their application to a dataset of argumentation problems. Therefore, the key contributions of this paper are: a more general semantics for functor-free ProbLog programs, its implementation into a probabilistic programming framework for both inference and parameter learning, and a novel approach to probabilistic argumentation problems based on such framework.'
publication: '*CoRR*'
links:
- name: URL
  url: https://arxiv.org/abs/2110.01990


url_pdf: https://arxiv.org/pdf/2110.01990.pdf
url_code: https://github.com/PietroTotis/smProblog
url_dataset:
url_poster:
url_project: 
url_slides:
url_source: 
url_video: 

---
<!-- 
### Problem

In this paper we propose a new approach to probabilistic argumentation problems based on probabilistic logic programming (PLP).
Probabilistic argumentation problems augment a traditional *abstract argumentation framework* (AAF) with probabilities: nodes are atomic arguments and edges denote the attack relation. 
Both arguments and relations can be associated with probabilities.

<img src="pargs.svg" width="600">

For probabilistic AAFs there are different approaches to define the semantics of probabilities and reasoning techniques specific to probabilistic AAFs.
On the contrary, PLP languages and systems aim at offering general purpose tools to reason and learn in structured domains under uncertainty.
In this paper we address the question as to whether PLP systems can be used to define semantics and reasoning techniques for probabilistic argumentation problems.
Our answer is divided in two parts: 
1. a mapping from probabilistic AAFs to probabilistic logic programs;
2. a PLP semantics and system, [smProbLog](https://github.com/PietroTotis/smProblog), which provide reasoning and learning tools suitable to this type of programs. 

### What do probabilities mean?

Probabilistic logic programs are logic programs in which some of the facts are annotated with probabilities.
For instance in this program the facts ``rain`` and ``wind`` are *probabilistic* because they belong to the program with some probability. 
Taking the umbrella or wearing the scarf are inferred from these two facts according to the logic rules.

```
0.4::rain.                  % probabilistic facts
0.7::wind.                   
umbrella :- rain, not wind. % logic rules
scarf :- rain.
scarf :- wind.
query(umbrella).            % compute the probability of taking the umbrella
```

Distribution semantics[^1] define the semantics of probabilities: each probabilistic fact {{<math>}}$p::f.${{</math>}}
represents an *independent* choice to include or not the fact in the program. 
A total choice is a set of choices for all facts: the *deterministic* program obtained by combining a total choice with the logical rules is a *possible world*.
The probability of success of a query is the sum of the probabilities of the possible worlds where queried atom can be derived to be true.

In probabilistic AAFs there are two approaches[^2] to define the semantics and reasoning techniques of probabilities:
1. The constellations approach.
2. The epistemic approach.

The constellations approach considers probabilities an expression of uncertainty over the structure of the graph. 
Similarly to distribution semantics, the probabilities induce a set of possible worlds corresponding to all possible subgraphs.
The probability of a subgraph is the combination of the probabilities of the chosen nodes and edges, and the probability of accepting an argument is the sum of the probabilities of the argument graphs where the argument is acceptable.
<img src="const.svg">
This approach however presents two issues regarding semantics:
1. the independence assumption of including or not an argument in the graph, while the goal of an AAF is to model their dependencies.
2. the semantics of the possible worlds where an attack is chosen but one of the two arguments involved is not (e.g. worlds on the right-hand side)

On the other hand, in the epistemic approach probabilities express *degrees of belief* in the arguments, and the structure of the graph is no longer uncertain.
Arguments with probability higher than 0.5 are considered accepted, otherwise rejected. 
Reasoning on epistemic argument graphs thus consists in finding a family of probability distribution that satisfies a given set of properties, e.g. coherency, rationality,..., with respect to the structure of the argument graph.
<img src="epistemic.svg"> 
For example the belief assignment in the picture is not rational because both {{<math>}}$a_1${{</math>}} and {{<math>}}$a_2${{</math>}} are accepted, but also the attack between the two receives a high degree of belief.

By mapping probabilistic argument graphs to PLP we introduce a novel perspective which combines the two approaches.
We model explicitly degrees of belief as in the epistemic approach, but we reason over this uncertainty with probabilistic logic programs and the distributions semantics, thus in terms of possible worlds as in the constellations approach.
The key points of our approach are:
1. The probability of an argument represents a belief bias *independent* of other arguments.
    It summarizes all the epistemic effects of the supporters of an argument which are not relevant to represent explicitly.
2. An attack {{<math>}}$(a,b)${{</math>}} with probability {{<math>}}$p${{</math>}} defines an *inhibition* of the belief in {{<math>}}$b${{</math>}} proportional to {{<math>}}$p${{</math>}} when $a$ is believed.


### Mapping probabilistic AAFs to PLP

Judea Pearl[^3] remarks how the combination of probability theory and graphs representing context dependencies are fundamental to model beliefs:
> We will also stress that probability theory is unique in its ability to process context-sensitive beliefs, and what makes the processing computationally feasible is that the information needed for specifying context dependencies can be represented by graphs and manipulated by local propagation.

We follow this principle in interpreting the argument graph as the representation of context dependencies between arguments:
1. We map arguments to logical atoms that are inferred from logical rules
2. We map arguments' probabilities to probabilistic facts which model a bias independent of other arguments. Any argument can be inferred from its bias.
3. We map attacks to logic rules with *negation in the head* annotated with the attack's probability.

```
0.6::bias(hotel_X).
0.8::bias(hotel_Y).
0.4::bias(expensive).
0.2::bias(noise).

arg(X) :- bias(X).

0.7::¬arg(hotel_Y) :- arg(hotel_X).
0.4::¬arg(hotel_X) :- arg(hotel_Y).
0.8::¬arg(hotel_Y) :- arg(noise).
0.9::¬arg(hotel_X) :- arg(expensive).

query(arg(X)).
```

Annotated rules are a syntactic feature that is equivalent to an additional probabilistic fact in the body, for instance:
```
0.8::umbrella :- rain, not wind.
```
is equivalent to:
```
0.8 :: remember.
umbrella :- remember, rain, not wind.
```
Moreover, negation in the head models the so-called *inhibition effect*, which expresses an inhibition of the belief of the head of the rule proportional to its probability.

```
0.3::friend_brings_umbrella.
¬umbrella :- friend_brings_umbrella.
```
is internally rewritten as:

```
0.3::friend_brings_umbrella.
umbrella :- umbrella_pos, umbrella_neg.
umbrella_pos :- remember, rain, not wind.
umbrella_neg :- friend_brings_umbrella.
```

<div style="display:flex;">
<img src="IE1.svg" width="400" style="margin-left:-10%">
<img src="IE2.svg" width="400" style="margin-left:-30%">
</div>

Moreover, the flexibility and expressivity of PLP can be exploited to encode more complex argumentation problems than basic AFFs, for instance expressing supports with regular rules (as with bias) or joint attacks or supports with rules with multiple arguments in the body.

### The joint probability distribution

The programs obtained from this mapping define a *joint probability distribution* over the arguments. 
The joint probability (belief) distribution induced by the argument graph resembles the description of N. Nilsson[^4] of how humans reason over beliefs:
> If we were to examine the relationships among all of our beliefs carefully, an impossible task in practice but one that is interesting to think about, we would see that some of them should make others more credible and some less. They would even compete among themselves with conflicting influences. We can imagine all of the beliefs in our large network of beliefs “fighting it out” to agree finally on the strength of each belief in the network. When they do finally agree, we say that the beliefs cohere.

The joint probability distribution can be analyzed with the typical PLP tools and algorithms offered by PLP systems.
Conditional probabilities, expressed by means of *evidence*, can be queried to study how the beliefs change when new information about the truth of the arguments is provided.
<iframe src="belief.html" title="Beliefs animation" height="400" width=700" frameBorder="0"></iframe>

Most probable explanation (MPE) queries return the most probable possible world where the given evidence holds. 
They can thus be used to find the set of beliefs which contribute the most to believing one or more arguments.

Finally, *learning from interpretations* (lfi) 
[^1]: [T. Sato, "A Statistical Learning Method for Logic Programs with Distribution Semantics", ICLP 1995.](https://rjida.meijo-u.ac.jp/reference/ICLP95.pdf)
[^2]: [A. Hunter, "A probabilistic approach to modelling uncertain logical arguments", Int. J. Approx. Reasoning, 2013](http://www0.cs.ucl.ac.uk/staff/a.hunter/papers/ijar12.pdf)
[^3]: [J. Pearl, "Probabilistic reasoning in intelligent systems: networks of plausible inference", Rev. 2. ed. Morgan Kaufmann, 2009](https://dl.acm.org/doi/10.5555/534975).
[^4]: [N. Nilsson, "Understanding Beliefs.", The MIT Press Essential Knowledge series. MIT Press, 2014](https://mitpress.mit.edu/9780262526432/understanding-beliefs/)
 -->
