# Notes concerning conversion of elegant-scipy to pandoc/r markdown

## Cheatsheet

Subscript: H~2~O
Superscript: ^137^Cs
Footnote: ^[footnote here]
Citation: `.bib` file, [@identifier] to cite
Un-numbered headings: # {-}
Figure : ![caption_text](path_to/url_of_figure)

## Hmm

 - No explicitly supported syntax for callouts in pandoc markdown
 - Solution for captioning figures created by code?
   * Elegant scipy currently uses html comments under code block that creates
     the figure
   * RMarkdown relies on Knitr, e.g.
     ```{python, out.width='25%', fig.align='center', fig.cap='my_caption'}
     plt.plot([1,2,3])
     ```
