+++
title = "Solving Combinatorial and Probabilistic Problems in Natural Language "
date = 2019-03-28T14:31:22+01:00
draft = false

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["Natural Language Processing", "Lifted Reasoning"]

# Project summary to display on homepage.
summary = ""

# Slides (optional).
#   Associate this page with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references
#   `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides = ""

# Optional external URL for project (replaces project detail page).
external_link = ""

# Links (optional).
url_pdf = ""
url_code = ""
url_dataset = ""
url_slides = ""
url_video = ""
url_poster = ""

# Custom links (optional).
#   Uncomment line below to enable. For multiple links, use the form `[{...}, {...}, {...}]`.
# links = [{icon_pack = "fab", icon="twitter", name="Follow", url = "https://twitter.com"}]

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
[image]
  # Caption (optional)
  caption = ""

  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point = ""
+++
This project aims to build a system capable of solving probabilistic and combinatorial problems from questions formulated in natural language. We are working on a dataset composed of common textbook problems that cover a wide range of situations and structures. An example:

> In a classroom there are 14 boys and 12 girls. 6 students are randomly selected for a school project: what is the probability that at least half of them are girls?

A sample of the data can be downloaded from the project page on [Problog's website](https://dtai.cs.kuleuven.be/problog/natural_language/).

This project was born from the IJCAI paper [Solving Probability Problems in Natural Language](https://lirias.kuleuven.be/bitstream/123456789/583588/1/nlp4plp.pdf). The work on probability problems has been further developed in the natural language processing part in collaboration with the [CLiPS](https://www.uantwerpen.be/en/research-groups/clips/) research center. The results of this collaboration are published in the paper [Mapping Probability Word Problems to Executable Representations]({{< ref "/publication/dblp-confemnlp-suster-ftkdrd-21/index" >}}).
The project on combinatorial math word problems resulted in the publication [Lifted Reasoning for Combinatorial Counting]({{< ref "/publication/Coso/index" >}}), where the language CoLa and the solver CoSo are presented. 


## CoLa and CoSo

CoLa and CoSo provide a framework for solving combinatorial counting problems. CoLa is a language to declare simple combinatorics problems, CoSo is a solver for CoLa and provides an explanation of the solution. 
The technical details and the scientific contributions are described in the publication:
> *Pietro Totis, Jesse Davis, Luc De Raedt, Angelika Kimmig: <br>
> Lifted Reasoning for Combinatorial Counting. J. Artif. Intell. Res. 76: 1-58 (2023)*

CoLa and CoSo can be used as a python package and they can be tested with a [jupyter notebook](https://github.com/PietroTotis/CoSo/blob/master/VisCoSo.ipynb). More details about the installation and the code can be found in the [Github repository](https://github.com/PietroTotis/CoSo).

With this package combinatorics math word problem can be solved and the solving process can be visualized in its reasoning steps. For example:

> A kit of toy shapes contains five triangles and two squares. One triangle and one square are red. Another triangle and the other square are blue, and the remaining triangles are green. In how many different rows of four objects can the shapes be arranged if the two squares are included and the second object is green?

CoSo can produce a visual representation of the problem solving strategy used to solve the problem, for example the resolution of the problem is represented as follows.


<!-- <iframe style="border: 0; width:100%; height:5000px" scrolling="no" onload="resizeIframe(this)" src="coso.html" title="CoSo"></iframe>  -->


<link rel="stylesheet" href="viscoso.css">
<div class="accordion">
      <div class="inline-solution">
        <i class="vsc-icon fa-solid fa-file-alt"></i>
        <h2 class="problem-lab">Problem</h2>
      </div>
      <div class="main-content" id="main-content">
        <div class="caption">
          <i class="vsc-icon fa-solid fa-info-circle"></i>
          <p class="caption-text">Root problem</p>
        </div>
        <div class="configuration">
          <div class="accordion">
            <input type="checkbox" class="control" id="handle1" name="collapse1" />
            <div class="handle">
              <div class="inline-solution">
                <i class="vsc-icon fa-solid fa-shapes"></i>
                <p class="inline-num">Universe</p>
              </div>
              <label for="handle1" class="vsc-lab"></label>
            </div>
            <div class="collapsable configuration">
              <table class="histogram">
                <tr>
                  <td class="ylabel">squares</td>
                  <td class="hcell" style="background-color: #b48ead">r2</td>
                  <td class="hcell" style="background-color: #b48ead">b2</td>
                </tr>
                <tr>
                  <td class="ylabel">(triangles) ∧ (¬green)</td>
                  <td class="hcell" style="background-color: #ebcb8b">r1</td>
                  <td class="hcell" style="background-color: #ebcb8b">b1</td>
                </tr>
                <tr>
                  <td class="ylabel">green</td>
                  <td class="hcell" style="background-color: #a3be8c">green</td>
                  <td class="hcell" style="background-color: #a3be8c">green</td>
                  <td class="hcell" style="background-color: #a3be8c">green</td>
                </tr>
              </table>
              <div class="accordion">
                <input type="checkbox" class="control" id="handle2" name="collapse2" />
                <div class="handle">
                  <div class="inline-solution">
                    <p class="inline-num">CoLa</p>
                  </div>
                  <label for="handle2" class="vsc-lab"></label>
                </div>
                <div class="collapsable">
                  <pre>universe (squares) ∨ (triangles) = {r2, b2, r1, b1, green, green, green}; 
property squares = {r2, b2}; 
property (triangles) ∧ (¬green) = {r1, b1}; 
property green = {green, green, green}; 
</pre>
                </div>
              </div>
            </div>
          </div>
          <div class="accordion">
            <input type="checkbox" class="control" id="handle3" name="collapse3" />
            <div class="handle">
              <div class="inline-solution">
                <i class="vsc-icon fa-solid fa-sitemap"></i>
                <p class="inline-num">Configuration</p>
              </div>
              <label for="handle3" class="vsc-lab"></label>
            </div>
            <div class="collapsable configuration">
              <table class="histogram">
                <tr>
                  <td class="slot" style="background-color: transparent">1</td>
                  <td class="slot" style="background-color: transparent">2</td>
                  <td class="slot" style="background-color: transparent">3</td>
                  <td class="slot" style="background-color: transparent">4</td>
                </tr>
              </table>
              <div class="accordion">
                <input type="checkbox" class="control" id="handle4" name="collapse4" />
                <div class="handle">
                  <div class="inline-solution">
                    <p class="inline-num">CoLa</p>
                  </div>
                  <label for="handle4" class="vsc-lab"></label>
                </div>
                <div class="collapsable">
                  <pre>permutation (size == 4) of entity universe (perm)</pre>
                </div>
              </div>
            </div>
          </div>
          <div class="accordion">
            <input type="checkbox" class="control" id="handle5" name="collapse5" />
            <div class="handle">
              <div class="inline-solution">
                <i class="vsc-icon fa-solid fa-ban"></i>
                <p class="inline-num">Constraints</p>
              </div>
              <label for="handle5" class="vsc-lab"></label>
            </div>
            <div class="collapsable configuration">
              <table class="histogram">
                <tr>
                  <td class="slot">2</td>
                  <td>
                    <i class="vsc-icon fa-solid fa-arrow-left"></i>
                  </td>
                  <td class="hcell" style="background-color: #a3be8c"></td>
                  <td class="ylabel">green</td>
                </tr>
              </table>
              <table class="histogram">
                <tr>
                  <td>
                    <i class="vsc-icon fa-solid fa-sitemap"></i>
                  </td>
                  <td>
                    <i class="vsc-icon fa-solid fa-arrow-right"></i>
                  </td>
                  <td class="constr-cell" style="background-color: #b48ead; border-color: #b48ead"></td>
                  <td class="constr-cell" style="background-color: #b48ead; border-color: #b48ead"></td>
                </tr>
              </table>
              <div class="accordion">
                <input type="checkbox" class="control" id="handle6" name="collapse6" />
                <div class="handle">
                  <div class="inline-solution">
                    <p class="inline-num">CoLa</p>
                  </div>
                  <label for="handle6" class="vsc-lab"></label>
                </div>
                <div class="collapsable">
                  <pre>Position 2: green; 
Nr. squares = 2; 
</pre>
                </div>
              </div>
            </div>
          </div>
        </div>
        <input type="checkbox" class="control" id="sol_1" name="sol_1" />
        <label for="sol_1" class="solution">
          <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
          <p class="inline-num">18</p>
        </label>
        <div class="collapsable Zerosubproblems">
          <div class="content-line"></div>
          <div class="accordions">
            <div class="accordion">
              <input type="checkbox" class="control" id="handle7" name="collapse7" />
              <div class="handle">
                <div class="inline-solution">
                  <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                  <p class="inline-num">18</p>
                </div>
                <label for="handle7" class="vsc-lab"></label>
              </div>
              <div class="collapsable">
                <div class="content-line"></div>
                <div class="vs-container">
                  <div class="caption">
                    <i class="vsc-icon fa-solid fa-info-circle"></i>
                    <p class="caption-text">Configuration of size 4</p>
                  </div>
                  <div class="configuration">
                    <div class="accordion">
                      <input type="checkbox" class="control" id="handle8" name="collapse8" />
                      <div class="handle">
                        <div class="inline-solution">
                          <i class="vsc-icon fa-solid fa-shapes"></i>
                          <p class="inline-num">Universe</p>
                        </div>
                        <label for="handle8" class="vsc-lab"></label>
                      </div>
                      <div class="collapsable configuration">
                        <table class="histogram">
                          <tr>
                            <td class="ylabel">(triangles) ∧ (¬green)</td>
                            <td class="hcell" style="background-color: #ebcb8b">r1</td>
                            <td class="hcell" style="background-color: #ebcb8b">b1</td>
                          </tr>
                          <tr>
                            <td class="ylabel">squares</td>
                            <td class="hcell" style="background-color: #b48ead">r2</td>
                            <td class="hcell" style="background-color: #b48ead">b2</td>
                          </tr>
                          <tr>
                            <td class="ylabel">green</td>
                            <td class="hcell" style="background-color: #a3be8c">green</td>
                            <td class="hcell" style="background-color: #a3be8c">green</td>
                            <td class="hcell" style="background-color: #a3be8c">green</td>
                          </tr>
                        </table>
                        <div class="accordion">
                          <input type="checkbox" class="control" id="handle9" name="collapse9" />
                          <div class="handle">
                            <div class="inline-solution">
                              <p class="inline-num">CoLa</p>
                            </div>
                            <label for="handle9" class="vsc-lab"></label>
                          </div>
                          <div class="collapsable">
                            <pre>universe (squares) ∨ (triangles) = {r2, b2, r1, b1, green, green, green}; 
property (triangles) ∧ (¬green) = {r1, b1}; 
property squares = {r2, b2}; 
property green = {green, green, green}; 
</pre>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="accordion">
                      <input type="checkbox" class="control" id="handle10" name="collapse10" />
                      <div class="handle">
                        <div class="inline-solution">
                          <i class="vsc-icon fa-solid fa-sitemap"></i>
                          <p class="inline-num">Configuration</p>
                        </div>
                        <label for="handle10" class="vsc-lab"></label>
                      </div>
                      <div class="collapsable configuration">
                        <table class="histogram">
                          <tr>
                            <td class="slot" style="background-color: transparent">1</td>
                            <td class="slot" style="background-color: transparent">2</td>
                            <td class="slot" style="background-color: transparent">3</td>
                            <td class="slot" style="background-color: transparent">4</td>
                          </tr>
                        </table>
                        <div class="accordion">
                          <input type="checkbox" class="control" id="handle11" name="collapse11" />
                          <div class="handle">
                            <div class="inline-solution">
                              <p class="inline-num">CoLa</p>
                            </div>
                            <label for="handle11" class="vsc-lab"></label>
                          </div>
                          <div class="collapsable">
                            <pre>Obj 1:  (squares) ∨ (triangles); 
Obj 2:  (squares) ∨ (triangles); 
Obj 3:  (squares) ∨ (triangles); 
Obj 4:  (squares) ∨ (triangles); 
</pre>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="accordion">
                      <input type="checkbox" class="control" id="handle12" name="collapse12" />
                      <div class="handle">
                        <div class="inline-solution">
                          <i class="vsc-icon fa-solid fa-ban"></i>
                          <p class="inline-num">Constraints</p>
                        </div>
                        <label for="handle12" class="vsc-lab"></label>
                      </div>
                      <div class="collapsable configuration">
                        <table class="histogram">
                          <tr>
                            <td class="slot">2</td>
                            <td>
                              <i class="vsc-icon fa-solid fa-arrow-left"></i>
                            </td>
                            <td class="hcell" style="background-color: #a3be8c"></td>
                            <td class="ylabel">green</td>
                          </tr>
                        </table>
                        <table class="histogram">
                          <tr>
                            <td>
                              <i class="vsc-icon fa-solid fa-sitemap"></i>
                            </td>
                            <td>
                              <i class="vsc-icon fa-solid fa-arrow-right"></i>
                            </td>
                            <td class="constr-cell" style="background-color: #b48ead; border-color: #b48ead"></td>
                            <td class="constr-cell" style="background-color: #b48ead; border-color: #b48ead"></td>
                          </tr>
                        </table>
                        <div class="accordion">
                          <input type="checkbox" class="control" id="handle13" name="collapse13" />
                          <div class="handle">
                            <div class="inline-solution">
                              <p class="inline-num">CoLa</p>
                            </div>
                            <label for="handle13" class="vsc-lab"></label>
                          </div>
                          <div class="collapsable">
                            <pre>Position 2: green; 
Nr. squares = 2; 
</pre>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                  <input type="checkbox" class="control" id="sol_2" name="sol_2" />
                  <label for="sol_2" class="solution">
                    <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                    <p class="inline-num">18</p>
                  </label>
                  <div class="collapsable subproblems">
                    <div class="content-line"></div>
                    <div class="accordions">
                      <div class="shatter">
                        <div class="row">
                          <div class="accordion">
                            <input type="checkbox" class="control" id="handle14" name="collapse14" />
                            <div class="handle">
                              <div class="inline-solution">
                                <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                                <p class="inline-num">1</p>
                              </div>
                              <label for="handle14" class="vsc-lab"></label>
                            </div>
                            <div class="collapsable">
                              <div class="content-line"></div>
                              <div class="vs-container">
                                <div class="caption">
                                  <i class="vsc-icon fa-solid fa-info-circle"></i>
                                  <p class="caption-text">Left split: case 1 green are s.t. [Nr. squares = 0, Nr. green = 1, Nr. ¬green = 0]</p>
                                </div>
                                <div class="configuration">
                                  <div class="accordion">
                                    <input type="checkbox" class="control" id="handle15" name="collapse15" />
                                    <div class="handle">
                                      <div class="inline-solution">
                                        <i class="vsc-icon fa-solid fa-shapes"></i>
                                        <p class="inline-num">Universe</p>
                                      </div>
                                      <label for="handle15" class="vsc-lab"></label>
                                    </div>
                                    <div class="collapsable configuration">
                                      <table class="histogram">
                                        <tr>
                                          <td class="ylabel">squares</td>
                                          <td class="hcell" style="background-color: #b48ead">r2</td>
                                          <td class="hcell" style="background-color: #b48ead">b2</td>
                                        </tr>
                                        <tr>
                                          <td class="ylabel">(triangles) ∧ (¬green)</td>
                                          <td class="hcell" style="background-color: #ebcb8b">r1</td>
                                          <td class="hcell" style="background-color: #ebcb8b">b1</td>
                                        </tr>
                                        <tr>
                                          <td class="ylabel">green</td>
                                          <td class="hcell" style="background-color: #a3be8c">green</td>
                                          <td class="hcell" style="background-color: #a3be8c">green</td>
                                          <td class="hcell" style="background-color: #a3be8c">green</td>
                                        </tr>
                                      </table>
                                      <div class="accordion">
                                        <input type="checkbox" class="control" id="handle16" name="collapse16" />
                                        <div class="handle">
                                          <div class="inline-solution">
                                            <p class="inline-num">CoLa</p>
                                          </div>
                                          <label for="handle16" class="vsc-lab"></label>
                                        </div>
                                        <div class="collapsable">
                                          <pre>universe green = {green, green, green}; 
property squares = {r2, b2}; 
property (triangles) ∧ (¬green) = {r1, b1}; 
</pre>
                                        </div>
                                      </div>
                                    </div>
                                  </div>
                                  <div class="accordion">
                                    <input type="checkbox" class="control" id="handle17" name="collapse17" />
                                    <div class="handle">
                                      <div class="inline-solution">
                                        <i class="vsc-icon fa-solid fa-sitemap"></i>
                                        <p class="inline-num">Configuration</p>
                                      </div>
                                      <label for="handle17" class="vsc-lab"></label>
                                    </div>
                                    <div class="collapsable configuration">
                                      <table class="histogram">
                                        <tr>
                                          <td class="slot" style="background-color: #a3be8c">1</td>
                                        </tr>
                                      </table>
                                      <div class="accordion">
                                        <input type="checkbox" class="control" id="handle18" name="collapse18" />
                                        <div class="handle">
                                          <div class="inline-solution">
                                            <p class="inline-num">CoLa</p>
                                          </div>
                                          <label for="handle18" class="vsc-lab"></label>
                                        </div>
                                        <div class="collapsable">
                                          <pre>Obj 1:  green; 
</pre>
                                        </div>
                                      </div>
                                    </div>
                                  </div>
                                  <div class="accordion">
                                    <input type="checkbox" class="control" id="handle19" name="collapse19" />
                                    <div class="handle">
                                      <div class="inline-solution">
                                        <i class="vsc-icon fa-solid fa-ban"></i>
                                        <p class="inline-num">Constraints</p>
                                      </div>
                                      <label for="handle19" class="vsc-lab"></label>
                                    </div>
                                    <div class="collapsable configuration">
                                      <table class="histogram"></table>
                                      <table class="histogram">
                                        <tr>
                                          <td>
                                            <i class="vsc-icon fa-solid fa-sitemap"></i>
                                          </td>
                                          <td>
                                            <i class="vsc-icon fa-solid fa-arrow-right"></i>
                                          </td>
                                          <td class="constr-cell" style="border-color: #b48ead">
                                            <i class="vsc-icon fa-solid fa-x"></i>
                                          </td>
                                        </tr>
                                        <tr>
                                          <td>
                                            <i class="vsc-icon fa-solid fa-sitemap"></i>
                                          </td>
                                          <td>
                                            <i class="vsc-icon fa-solid fa-arrow-right"></i>
                                          </td>
                                          <td class="constr-cell" style="background-color: #a3be8c; border-color: #a3be8c"></td>
                                        </tr>
                                        <tr>
                                          <td>
                                            <i class="vsc-icon fa-solid fa-sitemap"></i>
                                          </td>
                                          <td>
                                            <i class="vsc-icon fa-solid fa-arrow-right"></i>
                                          </td>
                                          <td class="constr-cell" style="border-color: #81a1c1">
                                            <i class="vsc-icon fa-solid fa-x"></i>
                                          </td>
                                        </tr>
                                      </table>
                                      <div class="accordion">
                                        <input type="checkbox" class="control" id="handle20" name="collapse20" />
                                        <div class="handle">
                                          <div class="inline-solution">
                                            <p class="inline-num">CoLa</p>
                                          </div>
                                          <label for="handle20" class="vsc-lab"></label>
                                        </div>
                                        <div class="collapsable">
                                          <pre>Nr. squares = 0; 
Nr. green = 1; 
Nr. ¬green = 0; 
</pre>
                                        </div>
                                      </div>
                                    </div>
                                  </div>
                                </div>
                                <input type="checkbox" class="control" id="sol_3" name="sol_3" />
                                <label for="sol_3" class="solution">
                                  <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                                  <p class="inline-num">1</p>
                                </label>
                                <div class="collapsable">
                                  <div class="content-line"></div>
                                  <div class="count-description">
                                    <i class="vsc-icon fa-solid fa-calculator"></i>
                                    <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                                    <p class="inline-num">$$\frac{\texttip{ \binom{ 0 }{ 0 } }{ Choose 0 of 0 (distinguishable) empty for 1 object(s) } \cdot \texttip{ 1! }{ Permutations of 1 green }}{\texttip{ 1! }{ Extra permutations of (indist.) green }}$$</p>
                                  </div>
                                </div>
                              </div>
                            </div>
                          </div>
                          <div class="accordion">
                            <input type="checkbox" class="control" id="handle21" name="collapse21" />
                            <div class="handle">
                              <div class="inline-solution">
                                <i class="vsc-icon fa-solid fa-times"></i>
                                <p class="inline-num">18</p>
                              </div>
                              <label for="handle21" class="vsc-lab"></label>
                            </div>
                            <div class="collapsable">
                              <div class="content-line"></div>
                              <div class="vs-container">
                                <div class="caption">
                                  <i class="vsc-icon fa-solid fa-info-circle"></i>
                                  <p class="caption-text">Right split removing 1 green</p>
                                </div>
                                <div class="configuration">
                                  <div class="accordion">
                                    <input type="checkbox" class="control" id="handle22" name="collapse22" />
                                    <div class="handle">
                                      <div class="inline-solution">
                                        <i class="vsc-icon fa-solid fa-shapes"></i>
                                        <p class="inline-num">Universe</p>
                                      </div>
                                      <label for="handle22" class="vsc-lab"></label>
                                    </div>
                                    <div class="collapsable configuration">
                                      <table class="histogram">
                                        <tr>
                                          <td class="ylabel">squares</td>
                                          <td class="hcell" style="background-color: #b48ead">r2</td>
                                          <td class="hcell" style="background-color: #b48ead">b2</td>
                                        </tr>
                                        <tr>
                                          <td class="ylabel">triangles</td>
                                          <td class="hcell" style="background-color: #d08770">r1</td>
                                          <td class="hcell" style="background-color: #d08770">b1</td>
                                          <td class="hcell" style="background-color: #d08770">green</td>
                                          <td class="hcell" style="background-color: #d08770">green</td>
                                          <td class="hcell" style="background-color: #d08770">green</td>
                                        </tr>
                                        <tr>
                                          <td class="ylab"></td>
                                          <td class="xlab"></td>
                                          <td class="xlab"></td>
                                          <td class="xlab"></td>
                                          <td class="xlab"></td>
                                          <td class="xlab">5</td>
                                        </tr>
                                      </table>
                                      <div class="accordion">
                                        <input type="checkbox" class="control" id="handle23" name="collapse23" />
                                        <div class="handle">
                                          <div class="inline-solution">
                                            <p class="inline-num">CoLa</p>
                                          </div>
                                          <label for="handle23" class="vsc-lab"></label>
                                        </div>
                                        <div class="collapsable">
                                          <pre>universe (squares) ∨ (triangles) = {r2, b2, r1, b1, green, green}; 
property squares = {r2, b2}; 
property triangles = {r1, b1, green, green, green}; 
</pre>
                                        </div>
                                      </div>
                                    </div>
                                  </div>
                                  <div class="accordion">
                                    <input type="checkbox" class="control" id="handle24" name="collapse24" />
                                    <div class="handle">
                                      <div class="inline-solution">
                                        <i class="vsc-icon fa-solid fa-sitemap"></i>
                                        <p class="inline-num">Configuration</p>
                                      </div>
                                      <label for="handle24" class="vsc-lab"></label>
                                    </div>
                                    <div class="collapsable configuration">
                                      <table class="histogram">
                                        <tr>
                                          <td class="slot" style="background-color: transparent">1</td>
                                          <td class="slot" style="background-color: transparent">2</td>
                                          <td class="slot" style="background-color: transparent">3</td>
                                        </tr>
                                      </table>
                                      <div class="accordion">
                                        <input type="checkbox" class="control" id="handle25" name="collapse25" />
                                        <div class="handle">
                                          <div class="inline-solution">
                                            <p class="inline-num">CoLa</p>
                                          </div>
                                          <label for="handle25" class="vsc-lab"></label>
                                        </div>
                                        <div class="collapsable">
                                          <pre>Obj 1:  (squares) ∨ (triangles); 
Obj 2:  (squares) ∨ (triangles); 
Obj 3:  (squares) ∨ (triangles); 
</pre>
                                        </div>
                                      </div>
                                    </div>
                                  </div>
                                  <div class="accordion">
                                    <input type="checkbox" class="control" id="handle26" name="collapse26" />
                                    <div class="handle">
                                      <div class="inline-solution">
                                        <i class="vsc-icon fa-solid fa-ban"></i>
                                        <p class="inline-num">Constraints</p>
                                      </div>
                                      <label for="handle26" class="vsc-lab"></label>
                                    </div>
                                    <div class="collapsable configuration">
                                      <table class="histogram"></table>
                                      <table class="histogram">
                                        <tr>
                                          <td>
                                            <i class="vsc-icon fa-solid fa-sitemap"></i>
                                          </td>
                                          <td>
                                            <i class="vsc-icon fa-solid fa-arrow-right"></i>
                                          </td>
                                          <td class="constr-cell" style="background-color: #b48ead; border-color: #b48ead"></td>
                                          <td class="constr-cell" style="background-color: #b48ead; border-color: #b48ead"></td>
                                          <td class="constr-cell-maybe" style="border-color: #b48ead"></td>
                                        </tr>
                                      </table>
                                      <div class="accordion">
                                        <input type="checkbox" class="control" id="handle27" name="collapse27" />
                                        <div class="handle">
                                          <div class="inline-solution">
                                            <p class="inline-num">CoLa</p>
                                          </div>
                                          <label for="handle27" class="vsc-lab"></label>
                                        </div>
                                        <div class="collapsable">
                                          <pre>Nr. squares in [2, 3]; 
</pre>
                                        </div>
                                      </div>
                                    </div>
                                  </div>
                                </div>
                                <input type="checkbox" class="control" id="sol_4" name="sol_4" />
                                <label for="sol_4" class="solution">
                                  <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                                  <p class="inline-num">18</p>
                                </label>
                                <div class="collapsable subproblems">
                                  <div class="content-line"></div>
                                  <div class="accordions">
                                    <div class="shatter">
                                      <div class="row">
                                        <div class="accordion">
                                          <input type="checkbox" class="control" id="handle28" name="collapse28" />
                                          <div class="handle">
                                            <div class="inline-solution">
                                              <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                                              <p class="inline-num">2</p>
                                            </div>
                                            <label for="handle28" class="vsc-lab"></label>
                                          </div>
                                          <div class="collapsable">
                                            <div class="content-line"></div>
                                            <div class="vs-container">
                                              <div class="caption">
                                                <i class="vsc-icon fa-solid fa-info-circle"></i>
                                                <p class="caption-text">Left split: case 2 squares are s.t. [Nr. squares = 2]</p>
                                              </div>
                                              <div class="configuration">
                                                <div class="accordion">
                                                  <input type="checkbox" class="control" id="handle29" name="collapse29" />
                                                  <div class="handle">
                                                    <div class="inline-solution">
                                                      <i class="vsc-icon fa-solid fa-shapes"></i>
                                                      <p class="inline-num">Universe</p>
                                                    </div>
                                                    <label for="handle29" class="vsc-lab"></label>
                                                  </div>
                                                  <div class="collapsable configuration">
                                                    <table class="histogram">
                                                      <tr>
                                                        <td class="ylabel">squares</td>
                                                        <td class="hcell" style="background-color: #b48ead">r2</td>
                                                        <td class="hcell" style="background-color: #b48ead">b2</td>
                                                      </tr>
                                                      <tr>
                                                        <td class="ylabel">triangles</td>
                                                        <td class="hcell" style="background-color: #d08770">r1</td>
                                                        <td class="hcell" style="background-color: #d08770">b1</td>
                                                        <td class="hcell" style="background-color: #d08770">green</td>
                                                        <td class="hcell" style="background-color: #d08770">green</td>
                                                        <td class="hcell" style="background-color: #d08770">green</td>
                                                      </tr>
                                                      <tr>
                                                        <td class="ylab"></td>
                                                        <td class="xlab"></td>
                                                        <td class="xlab"></td>
                                                        <td class="xlab"></td>
                                                        <td class="xlab"></td>
                                                        <td class="xlab">5</td>
                                                      </tr>
                                                    </table>
                                                    <div class="accordion">
                                                      <input type="checkbox" class="control" id="handle30" name="collapse30" />
                                                      <div class="handle">
                                                        <div class="inline-solution">
                                                          <p class="inline-num">CoLa</p>
                                                        </div>
                                                        <label for="handle30" class="vsc-lab"></label>
                                                      </div>
                                                      <div class="collapsable">
                                                        <pre>universe squares = {r2, b2}; 
property triangles = {r1, b1, green, green, green}; 
</pre>
                                                      </div>
                                                    </div>
                                                  </div>
                                                </div>
                                                <div class="accordion">
                                                  <input type="checkbox" class="control" id="handle31" name="collapse31" />
                                                  <div class="handle">
                                                    <div class="inline-solution">
                                                      <i class="vsc-icon fa-solid fa-sitemap"></i>
                                                      <p class="inline-num">Configuration</p>
                                                    </div>
                                                    <label for="handle31" class="vsc-lab"></label>
                                                  </div>
                                                  <div class="collapsable configuration">
                                                    <table class="histogram">
                                                      <tr>
                                                        <td class="slot" style="background-color: #b48ead">1</td>
                                                        <td class="slot" style="background-color: #b48ead">2</td>
                                                      </tr>
                                                    </table>
                                                    <div class="accordion">
                                                      <input type="checkbox" class="control" id="handle32" name="collapse32" />
                                                      <div class="handle">
                                                        <div class="inline-solution">
                                                          <p class="inline-num">CoLa</p>
                                                        </div>
                                                        <label for="handle32" class="vsc-lab"></label>
                                                      </div>
                                                      <div class="collapsable">
                                                        <pre>Obj 1:  squares; 
Obj 2:  squares; 
</pre>
                                                      </div>
                                                    </div>
                                                  </div>
                                                </div>
                                                <div class="accordion">
                                                  <input type="checkbox" class="control" id="handle33" name="collapse33" />
                                                  <div class="handle">
                                                    <div class="inline-solution">
                                                      <i class="vsc-icon fa-solid fa-ban"></i>
                                                      <p class="inline-num">Constraints</p>
                                                    </div>
                                                    <label for="handle33" class="vsc-lab"></label>
                                                  </div>
                                                  <div class="collapsable configuration">
                                                    <table class="histogram"></table>
                                                    <table class="histogram">
                                                      <tr>
                                                        <td>
                                                          <i class="vsc-icon fa-solid fa-sitemap"></i>
                                                        </td>
                                                        <td>
                                                          <i class="vsc-icon fa-solid fa-arrow-right"></i>
                                                        </td>
                                                        <td class="constr-cell" style="background-color: #b48ead; border-color: #b48ead"></td>
                                                        <td class="constr-cell" style="background-color: #b48ead; border-color: #b48ead"></td>
                                                      </tr>
                                                    </table>
                                                    <div class="accordion">
                                                      <input type="checkbox" class="control" id="handle34" name="collapse34" />
                                                      <div class="handle">
                                                        <div class="inline-solution">
                                                          <p class="inline-num">CoLa</p>
                                                        </div>
                                                        <label for="handle34" class="vsc-lab"></label>
                                                      </div>
                                                      <div class="collapsable">
                                                        <pre>Nr. squares = 2; 
</pre>
                                                      </div>
                                                    </div>
                                                  </div>
                                                </div>
                                              </div>
                                              <input type="checkbox" class="control" id="sol_5" name="sol_5" />
                                              <label for="sol_5" class="solution">
                                                <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                                                <p class="inline-num">2</p>
                                              </label>
                                              <div class="collapsable">
                                                <div class="content-line"></div>
                                                <div class="count-description">
                                                  <i class="vsc-icon fa-solid fa-calculator"></i>
                                                  <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                                                  <p class="inline-num">$$\texttip{ 2! }{ Nr. orders for all objects }$$</p>
                                                </div>
                                              </div>
                                            </div>
                                          </div>
                                        </div>
                                        <div class="accordion">
                                          <input type="checkbox" class="control" id="handle35" name="collapse35" />
                                          <div class="handle">
                                            <div class="inline-solution">
                                              <i class="vsc-icon fa-solid fa-times"></i>
                                              <p class="inline-num">3</p>
                                            </div>
                                            <label for="handle35" class="vsc-lab"></label>
                                          </div>
                                          <div class="collapsable">
                                            <div class="content-line"></div>
                                            <div class="vs-container">
                                              <div class="caption">
                                                <i class="vsc-icon fa-solid fa-info-circle"></i>
                                                <p class="caption-text">Right split removing 2 squares</p>
                                              </div>
                                              <div class="configuration">
                                                <div class="accordion">
                                                  <input type="checkbox" class="control" id="handle36" name="collapse36" />
                                                  <div class="handle">
                                                    <div class="inline-solution">
                                                      <i class="vsc-icon fa-solid fa-shapes"></i>
                                                      <p class="inline-num">Universe</p>
                                                    </div>
                                                    <label for="handle36" class="vsc-lab"></label>
                                                  </div>
                                                  <div class="collapsable configuration">
                                                    <table class="histogram">
                                                      <tr>
                                                        <td class="ylabel">(squares) ∨ (triangles)</td>
                                                        <td class="hcell" style="background-color: #88c0d0">r1</td>
                                                        <td class="hcell" style="background-color: #88c0d0">b1</td>
                                                        <td class="hcell" style="background-color: #88c0d0">green</td>
                                                        <td class="hcell" style="background-color: #88c0d0">green</td>
                                                      </tr>
                                                    </table>
                                                    <div class="accordion">
                                                      <input type="checkbox" class="control" id="handle37" name="collapse37" />
                                                      <div class="handle">
                                                        <div class="inline-solution">
                                                          <p class="inline-num">CoLa</p>
                                                        </div>
                                                        <label for="handle37" class="vsc-lab"></label>
                                                      </div>
                                                      <div class="collapsable">
                                                        <pre>universe (squares) ∨ (triangles) = {r1, b1, green, green}; 
</pre>
                                                      </div>
                                                    </div>
                                                  </div>
                                                </div>
                                                <div class="accordion">
                                                  <input type="checkbox" class="control" id="handle38" name="collapse38" />
                                                  <div class="handle">
                                                    <div class="inline-solution">
                                                      <i class="vsc-icon fa-solid fa-sitemap"></i>
                                                      <p class="inline-num">Configuration</p>
                                                    </div>
                                                    <label for="handle38" class="vsc-lab"></label>
                                                  </div>
                                                  <div class="collapsable configuration">
                                                    <table class="histogram">
                                                      <tr>
                                                        <td class="slot" style="background-color: #88c0d0">1</td>
                                                      </tr>
                                                    </table>
                                                    <div class="accordion">
                                                      <input type="checkbox" class="control" id="handle39" name="collapse39" />
                                                      <div class="handle">
                                                        <div class="inline-solution">
                                                          <p class="inline-num">CoLa</p>
                                                        </div>
                                                        <label for="handle39" class="vsc-lab"></label>
                                                      </div>
                                                      <div class="collapsable">
                                                        <pre>Obj 1:  (squares) ∨ (triangles); 
</pre>
                                                      </div>
                                                    </div>
                                                  </div>
                                                </div>
                                              </div>
                                              <input type="checkbox" class="control" id="sol_6" name="sol_6" />
                                              <label for="sol_6" class="solution">
                                                <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                                                <p class="inline-num">3</p>
                                              </label>
                                              <div class="collapsable">
                                                <div class="content-line"></div>
                                                <div class="count-description">
                                                  <i class="vsc-icon fa-solid fa-calculator"></i>
                                                  <i class="vsc-icon fa-solid fa-equals fa-sm"></i>
                                                  <p class="inline-num">$$\frac{\texttip{ \binom{ 2 }{ 0 } }{ Choose 0 of 2 (distinguishable) ??? for 1 object(s) } \cdot \texttip{ 1! }{ Permutations of 1 (squares) ∨ (triangles) }}{\texttip{ 1! }{ Extra permutations of (indist.) ??? }} + \frac{\texttip{ \binom{ 2 }{ 1 } }{ Choose 1 of 2 (distinguishable) ??? for 1 object(s) } \cdot \texttip{ 1! }{ Permutations of 1 (squares) ∨ (triangles) }}{\texttip{ 0! }{ Extra permutations of (indist.) ??? }}$$</p>
                                                </div>
                                              </div>
                                            </div>
                                          </div>
                                        </div>
                                      </div>
                                    </div>
                                  </div>
                                </div>
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>