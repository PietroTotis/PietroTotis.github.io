---
# Documentation: https://wowchemy.com/docs/managing-content/

title: Efficient Knowledge Compilation Beyond Weighted Model Counting
subtitle: ''
summary: ''
authors:
- Rafael Kiesel
- Pietro Totis
- Angelika Kimmig
tags: [KRR, PLP, Journal]
categories: []
date: '2022-01-01'
lastmod: 2022-11-04T12:29:19+01:00
featured: false
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
publishDate: '2022-11-04T11:29:19.637273Z'
publication_types:
- '2'
abstract: 'Quantitative extensions of logic programming often require the solution of so called second level inference tasks, i.e., problems that involve a third operation, such as maximization or normalization, on top of addition and multiplication, and thus go beyond the well-known weighted or algebraic model counting setting of probabilistic logic programming under the distribution semantics. We introduce Second Level Algebraic Model Counting (2AMC) as a generic framework for this kind of problems. As 2AMC is to (algebraic) model counting what forall-exists-SAT is to propositional satisfiability, it is notoriously hard to solve. First level techniques based on Knowledge Compilation (KC) have been adapted for specific 2AMC instances by imposing variable order constraints on the resulting circuit. However, those constraints can severely increase the circuit size and thus decrease the efficiency of such approaches. We show that we can exploit the logical structure of a 2AMC problem to omit parts of these constraints, thus limiting the negative effect. Furthermore, we introduce and implement a strategy to generate a sufficient set of constraints statically, with a priori guarantees for the performance of KC. Our empirical evaluation on several benchmarks and tasks confirms that our theoretical results can translate into more efficient solving in practice.'
summary: "We introduce second level algebraic model counting (2AMC) problems, a framework generalizing several probabilistic inference task. We present a novel Knowledge Compilation technique to address the increased complexity of a 2AMC task with respect to first-level AMC problems."

publication: '*Theory and Practice of Logic Programming*'
publication_short: "*TPLP*"
doi: 10.1017/S147106842200014X
links:
- name: URL
  url: https://doi.org/10.1017/S147106842200014X


url_pdf: https://www.cambridge.org/core/services/aop-cambridge-core/content/view/B85D8CC591869EF970780E94C8B92D1B/S147106842200014Xa.pdf/efficient-knowledge-compilation-beyond-weighted-model-counting.pdf
url_code: https://github.com/raki123/aspmc
url_dataset:
url_poster:
url_project: 
url_slides:
url_source:
url_video: 

---
