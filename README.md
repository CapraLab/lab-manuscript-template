# Welcome to the Capra Lab Manuscript Template!  
This was created by the members of the [Capra Lab](http://www.capralab.org/) 2/2022 and finalized for LaTeX and MS Word by Evonne McArthur 3/2022. A LaTeX template formatted for Cell Press journals was added by Colin Brand 11/2023.

The goal of these documents is to help make formatting and writing a manuscript easier and more standardized. Some of these suggestions are subjective and there is ultimately no one-size-fits-all for writing a paper. However, this will hopefully serve as a great place to start.  

Feedback is welcome! The LaTeX template is [available on overleaf is here](https://www.overleaf.com/latex/templates/capra-lab-manuscript-template/mrtmxhjdyzvz).  
  
## Files
- `CapraLabManuscriptTemplate.pdf`: An example of the compiled LaTeX Manuscript with tips for organizing and writing a manuscript  
- `CapraLabManuscriptTemplate.docx`: Manuscript template in MS Word Format  
- `CapraLabManuscriptTemplate_withoutTips.docx`: Template in MS Word Format without the extra writing tips
- `latexTemplate/`  
  - `main_figs/`: folder for main text figures  
  - `supplement/`: folder and files (`0suppl_text.tex`,`1suppl_figs.tex`,`2suppl_tabs.tex`) for supplemental content  
    - `suppl_figs/`: folder for supplemental figs  
    - `suppl_tabs/`: folder for supplemental tabs  
  - `0main.tex`: Contains preamble (imported packages) and document organizational structure at the bottom (i.e. reads in and structures all the other files)  
  - `1titlepage.tex`: Info for the title page (title, authors, affils, abstract)  
  - `2intro.tex`: Introduction section  
  - `3results.tex`: Results section  
  - `4maintextFigs.tex`: Maintext figures & captions  
  - `5discussion.tex`: Discussion section  
  - `6methods.tex`: Methods section  
  - `helperFunctions.tex`: You can put any helper functions here. It includes functions for formatting figures, tables, and captions.  
  - `library.bib`: example bibliography file  
  - `REMOVEME_tips.tex`: Contains the text (gray-blue-purple text) for tips about each section, you can eventually delete this. See instructions below.  
  
## Using the MS Word Template  
1. Download `CapraLabManuscriptTemplate.docx`.  
2. Read through the tips for each section (gray-blue-purple text) and then delete them.  
3. Fill in the template with your content.  
4. For figures/tables, reference them using a descriptive "code name" (e.g. "genomeOverviewFig") so that if you rearrange figures, it is not a headache to renumber. At the VERY end, you can replace the code names with the figures in their final order.  
5. For references, use a citation manager with Word plugin (e.g. Zotero, Mendeley)  
6. Export as one large PDF (or two if you want to separate the main text and supplement).  
7. Publish!!  
  
## Using the LaTeX Template  
1. Either download `latexTemplate/` and use a compiler locally or access the template [on overleaf here](https://www.overleaf.com/latex/templates/capra-lab-manuscript-template/mrtmxhjdyzvz).  
2. Read through the tips for each section (gray-blue-purple text) and then delete the lines that input these tips: **\input{REMOVEME_tips}** in `0main.tex`, **\titleTips**, **\abstractTips** in `1titlepage.tex`, **\introTips** in `2intro.tex`, **\resultsTips** in `3results.tex`, **\captionTips** in `4maintextFigs.tex`, **\discussionTips** in `5discussion.tex`, **\methodsTips**, **\methodsDataTips**, **\methodsAnalysisTips** in `6methods.tex` and **\generalTips** in `0suppl_text.tex`. Then you can delete the entire file for these tips: `REMOVEME_tips.tex`.  
3. Fill in the template with your content in the relevant files.  
4. For figures/tables, reference them using a descriptive "code name". Follow the directions in `4maintextFigs.tex` or below for how to create & reference the figures. This will take care of all the formatting and numbering. If you want to change the format of the figures/tables/captions, you can edit the corresponding functions in `helperFunctions.tex`.  
5. For references, upload a custom `.bib` file from your reference manager. Overleaf has integration with certain systems for easier citations.  
6. Compile and export as a PDF. (For initial submission you just need the pdf, for final submission, you will submit the compiled documents as a zipped folder).  
7. Publish!!

## Using the Cell Press journal format LaTeX Template
Download ` Cell_Press_journal_format_latexTemplate/`, compile, and follow the instruction for the general use LaTeX template above.
  
### Extra details on using the LaTeX templates  
#### Creating figures, subfigures, and captions  
There are 6 functions in `helperFunctions.tex` that may be used for formatting figures, subfigures, tables, and captions. Note that, as the template is currently written, these all apply to "preassembled figures" where all panels (i.e. A, B, C) are included in one image or pdf file. 
  
- `\generateFigSubpanels`: Figure with subpanels  
- `\generateFig`: Figure without subpanels  
- `\generateSidewaysFigSubpanels`: Sideways fig and caption with subpanels  
- `\generateSidewaysFig`: Sideways fig and caption without subpanels  
- `\generateTab:` Table  
- `\generateSidewaysTab`: Sideways table and caption  
  
All functions take a "code name" that will be used to reference the figure/table, a path to the actual figure/table, the width of the figure/table, a main caption, and sub-caption(s) (if the figure has multiple panels, you will specify one sub-caption per panel). The width of the figure/table is specified by the proportion of the text's width (i.e. 1 is the full width, 0.5 is half-width). For the figure-related functions, you can optionally specify the angle of the figure (90 will rotate the figure, but not the caption).  
  
#### Putting the figures into the text  
To control where the figures go in the text, reference the figure with the command corresponding to its "code name" in the text where you want it to approximately appear: `\codeName`  
  
#### Referencing the figures  
Figure referencing can be implemented with [cleveref](https://ctan.org/pkg/cleveref?lang=en).  
  
- A single figure/table will be referenced as: `\cref{fig:figureCodeName}` `\cref{tab:tableCodeName}`  
- A subpanel of a figure will be referenced as: `\cref{fig:figureCodeName:A}`  
- Multiple figures or subpanels can be referenced as: `\cref{fig:figureCodeNameOne,fig:figureCodeNameTwo}`  
- A range of figures can be referenced as: `\crefrange{fig:figureCodeNameOne}{fig:figureCodeNameTwo}`  
  
#### Citations  
There are multiple ways to cite in LaTeX; each has unique pros and cons. The current default in this document is using BibLaTeX to generate the bibliography (because of its flexibility) with the commands from natbib. That way, if a journal does not accept BibLaTeX, you can easily convert to natbib because the commands are already in place. See [details here](https://tex.stackexchange.com/questions/25701/bibtex-vs-biber-and-biblatex-vs-natbib). In the preamble, there are instructions on how to use numeric citations or author-year citations. 

To cite references parenthetically, use `~\citep{citationKey1, citationKey2}`. To cite references in-text use `~\citet{citationKey3}`.  

#### Stylistic choices to consider
These are all options that can be edited in `0main.tex`

- Default LaTeX Serif font vs. Arial
- Line numbers on vs. off
- Line spacing (1.15 vs. 1 vs. 1.5 vs. 2)
- Author-year vs. numeric in-text citations
- Justified text vs. left-aligned (ragged right)
- How figures are referenced (Figure vs. Fig, bold vs. normal)
  
## Contact  
For feedback or other tips, please contact Tony Capra at [firstname]@[lastname]lab[dot]org or Evonne McArthur at [firstname][dot][lastname]@gmail[dot]com.
