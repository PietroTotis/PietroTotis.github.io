---
# Documentation: https://wowchemy.com/docs/managing-content/

title: Towards Distributed Computation of Answer Sets
subtitle: ''
summary: ''
authors:
- Marco De Bortoli
- Federico Igne
- Fabio Tardivo
- Pietro Totis
- Agostino Dovier
- Enrico Pontelli
tags: [KRR, Conference]
categories: []
date: '2019-01-01'
lastmod: 2022-11-04T12:29:20+01:00
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
publishDate: '2022-11-04T11:29:20.275341Z'
publication_types: ['paper-conference']
abstract: 'Answer Set Programming (ASP) is a logic programming language widely used in non-monotonic automated reasoning. Thanks to its popularity, in the last years there has been a great interest towards the developing of efficient solvers, required to deal with complex problems, like planning and NP problem-solving. These solvers can be unable to deal with programs that are “grounded” on huge amount of data, possibly resident in different sites. To address this problem, in this paper we present a distributed approach to ASP problems, which involves all the phases of the overall solving process: from a distributed grounder (which can also be used as a solver for stratified programs) to two different techniques to deal with the pure solving phase (for non-stratified program too), both of them using the non-standard graph coloring algorithm to characterize answer sets. We show three proposals for solving the issue, two of them developed with the high-level framework Apache Spark, while the third one is a C++ direct implementation of the first one.'
publication: '*Proceedings of the 34th Italian Conference on Computational Logic,
  Trieste, Italy, June 19-21, 2019*'
publication_short: '*CILC 2019*'
url_pdf: http://ceur-ws.org/Vol-2396/paper36.pdf
conference_page : https://cilc2019.units.it/
---

