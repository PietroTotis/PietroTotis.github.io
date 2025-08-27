---
# Documentation: https://wowchemy.com/docs/managing-content/

title: Mapping Probability Word Problems to Executable Representations
subtitle: ''
summary: ''
authors:
- Simon Suster
- Pieter Fivez
- Pietro Totis
- Angelika Kimmig
- Jesse Davis
- Luc De Raedt
- Walter Daelemans
tags: [NLP, KRR, PLP, Conference]
categories: []
date: '2021-01-01'
lastmod: 2022-11-04T12:29:20+01:00
featured: false
draft: false
show_breadcrumb: true

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
publishDate: '2022-11-04T11:29:19.948674Z'
publication_types: ['paper-conference']
abstract: 'While solving math word problems automatically has received considerable attention in the NLP community, few works have addressed probability word problems specifically. In this paper, we employ and analyse various neural
models for answering such word problems. In a two-step approach, the problem text is first mapped to a formal representation in a declarative language using a sequence-to-sequence model, and then the resulting representation
is executed using a probabilistic programming system to provide the answer. Our best performing model incorporates general-domain contextualised word representations that were finetuned using transfer learning on another in-domain dataset. We also apply end-to-end models to this task, which bring out the importance of the two-step approach in obtaining correct solutions to probability problems.'
summary: "We analyze different neural models to solve probability math word problems in two ways. First, to predict directly the answer in an end-to-end fashion. Second, to map the text to a formal representation used by a probabilistic programming system to compute the answer."
publication: '*Proceedings of the 2021 Conference on Empirical Methods in Natural
  Language Processing, EMNLP 2021, Virtual Event / Punta Cana, Dominican Republic,
  7-11 November, 2021*'
publication_short: "*EMNLP 2021*"
doi: 10.18653/v1/2021.emnlp-main.294
links:
- name: URL
  url: https://doi.org/10.18653/v1/2021.emnlp-main.294

url_pdf: https://aclanthology.org/2021.emnlp-main.294.pdf
url_code: 
url_dataset:
url_poster:
url_project: https://www.kuleuven.be/onderzoek/portaal/#/projecten/3E180082?lang=en&hl=en
url_slides:
url_source:
url_video: https://aclanthology.org/2021.emnlp-main.294.mp4
---
