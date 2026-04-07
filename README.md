# VUB LaTeX Template

This is a LaTeX template for academic reports using the VUB (Vrije Universiteit Brussel) style. I adapted the template from [Ruben De Smet](https://gitlab.com/rubdos/texlive-vub) and modified it to better fit my needs, to work better in VS Code, modular section files and automatic bibliography management. I tried to keep it as simple as possible and it can still be used with other LaTeX editors or Overleaf without any issues.
I also wrote this README to help you get started and to explain how to use the template. If you have any questions or suggestions for improvement, you can tell me or just create an issue or pull request on the GitHub page.


[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) 


## Quick Start

### Prerequisites
Before you can start writing, you have to make sure you have the necessary tools and packages installed. I recommend using a VS code based editor (such as [VS Code](https://code.visualstudio.com/), [VSconium](https://vscodium.com/)...), but you can also use other LaTeX editors or Overleaf. The main reasons why I recommend VS Code based editors are that there exists many useful extensions for Latex and it is very customizable. It also integrates well with Git for version control, you can easily manage your bibliography using Zotero and it also integrates AI quit well which can be really handy for formatting or debugging your LaTeX code (if you use this, make sure you acknowledge this in your paper). I also included a settings.json file so that is should work in vs code as intended without to much hassle. For this guide I will focus on the VS Code setup, but I will also provide instructions for other editors (such as TeXstudio) and Overleaf.

So before you start, make sure you have the following installed:
- **LaTeX Distribution**: [MiKTeX](https://miktex.org/) (Windows) or [TeX Live](https://www.tug.org/texlive/) (Linux/Mac)
- **LaTeX Packages**: Ensure the following essential packages are installed in your TeX distribution (most are included by default in full installations): `geometry`, `color`, `tikz`, `adjustbox`, `kvoptions`, `ifxetex`, `ifluatex`, `fontspec` (for XeLaTeX/LuaLaTeX), and `tex-gyre` (for the TeX Gyre Adventor font).
- **Perl**: Required by latexmk. [Strawberry Perl](http://strawberryperl.com/) (Windows). On macOS and Linux, Perl is normally pre-installed (if not, install via your package manager, e.g., `sudo apt install perl` or `brew install perl`).
- **VS Code based editor** (you can also use other LaTeX editors): With [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) extension, below I added a list of other recommended extensions to enhance your LaTeX writing experience in VS Code.
- **Fonts**: The template uses TeX Gyre Adventor, the official VUB font. It should be included in your TeX distribution, but if you want to install it manually, you can download it from [TeX Gyre](http://www.gust.org.pl/projects/e-foundry/tex-gyre/adventor) and install it on your system.

### Installing This Template

#### Option 1: Clone it from the repository (Recommended)
For this you have to have [Git](https://git-scm.com/install/) installed. This can be done in the VS Code's terminal itself or any terminal of your choice:
```bash
# Clone this repository in a new folder called "my-project"
git clone https://github.com/JonasBil/Latex-template-VUB.git my-project
cd my-project

```
Change `my-project` to whatever you want to name your project folder, if you want it in the folder itself you can change it to `.` so then you get:
```bash
# Clone this repository into the current folder
git clone https://github.com/JonasBil/Latex-template-VUB.git .
```


#### Option 2: Manual Download (If you don't want to use Git)

You can also download the repository as a ZIP file form the [GitHub Page](https://github.com/JonasBil/Latex-template-VUB) (click on the green **Code** button and select **Download ZIP**), then extract the contents to your desired location and compile `main.tex` using the run button in vs code, or compile manually (see instructions below).


#### Option 3: Using Overleaf

1. Click the green **Code** button at the top of this [GitHub repository](https://github.com/JonasBil/Latex-template-VUB) and select **Download ZIP**.
2. Go to [Overleaf](https://www.overleaf.com/) and click **New Project** $\rightarrow$ **Upload Project**.
3. Select the `.zip` file you downloaded.
4. Overleaf will automatically detect `main.tex` and compile your document. Both `pdfLaTeX` and `XeLaTeX` compilers will work correctly.

#### Option 4: Other LaTeX Editors (e.g., Texifier, TeXstudio, TeXShop)
I haven't tested this very well, but it should work fine as long as you set the main file to `main.tex` and ensure that your build sequence includes a BibTeX backend for the bibliography. The exact steps may vary depending on your editor, but generally:

1. Clone or download the repository to your local machine.
2. Open `main.tex` in your preferred editor.
3. Depending on your editor:
   - **Texifier / TeXstudio**: They will usually auto-detect your `main.tex` and let you build right away. Just make sure the build sequence runs a BibTeX backend (like Biber or standard BibTeX) along with `pdflatex` or `xelatex`.
   - **Build Configurations**: you can map the editor's build sequence to use the equivalent of `latexmk -pdf` to ensure both cross-references and bibliographies compile successfully.



## Recommended VS Code Extensions

The following extensions are recommended for a smooth LaTeX workflow in VS Code (In VS code you can create a new [**VS-code profile**](https://code.visualstudio.com/docs/editor/profiles) with these plugins, i really recommend doing this so you can easily switch between your LaTeX writing environment and your normal coding environment and this keeps everything organized):

- **[LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)** — The core extension for LaTeX in VS Code. Provides one-click PDF compilation (using the **green run** button or `Ctrl+Alt+B`), real-time error highlighting, SyncTeX support (click in the PDF to jump to the source and vice versa), auto-completion for `\cite{}`, `\ref{}`, and LaTeX commands, and a built-in PDF viewer. This template's `.vscode/settings.json` is pre-configured for it and should not be deleted!.
- **[LTeX](https://marketplace.visualstudio.com/items?itemName=valentjn.vscode-ltex)** — Grammar and spell checking powered by LanguageTool. Works directly in `.tex` files and understands LaTeX syntax, so it won't flag commands as spelling errors. Supports multiple languages.
- **[LaTeX Utilities](https://marketplace.visualstudio.com/items?itemName=tecosaur.latex-utilities)** — Adds quality-of-life features on top of LaTeX Workshop: live snippet previews (if you hover over f.e a image or equation snippet, you will see a preview), magic comments, and formatted paste (e.g., pasting a table from Excel auto-generates a `tabular` environment).
- **[Zotero LaTeX](https://marketplace.visualstudio.com/items?itemName=bnavetta.zoterolatex)** — Enables cite-as-you-write by searching your Zotero library directly from VS Code and inserting `\cite{}` keys.

To install these extensions all at once, run in a terminal:
```bash
code --install-extension James-Yu.latex-workshop
code --install-extension valentjn.vscode-ltex
code --install-extension tecosaur.latex-utilities
code --install-extension bnavetta.zoterolatex
```
Or you can search for them in the VS Code Extensions Marketplace and install them with a click.


## Writing & Building Your Document
When everything is installed and set up, you can start writing your document by editing the `main.tex` file and the **section files** in the `sections/` folder. The template is structured to keep your content organized and modular, so you can focus on writing without worrying about formatting. The `main.tex` file serves as the **main entry point** and includes the preamble, title page setup, and the structure of your document. The **actual content** of each section is stored in separate `.tex` files within the `sections/` folder, which are included in `main.tex` using `\input{}` commands. If you want to add more sections, simply create a new `.tex` file in the `sections/` folder and include it in `main.tex` as the other sections. When compiling (or building) the document, the **resulting pdf** is generated together with the other output files in a `build/` folder (**this is created the first time you build the document**). Below is a step-by-step guide to get you started:

### 1. Update Document Information

Edit the preamble, title and author information in `main.tex`:

```latex
%! Author = Your Name
%! Date = DD/MM/YYYY

\title{Your Document Title}
\faculty{Sciences and Bio-Engineering Sciences}  % Your VUB faculty
\author{Your Name}
```

Also update the footer:
```latex
\fancyfoot[LO, RE]{Your Name}  % Change to your name
```

**Changing the Title Page (Custom Commands)**
If you want to customize the title page further, the `vub` style packages (`vub.sty` and `vubprivate.sty`) provide several custom commands to format your document. You can use these commands in the  `main.tex` to set additional information or customize the appearance of the title page. Here are some of the key commands you can use:

Title Page Commands (use in main.tex):
- `\faculty{Name}`: Set your faculty name (e.g., `\faculty{Engineering Sciences}`).
- `\subtitle{Text}`: Add a subtitle below the main document title.
- `\pretitle{Text}`: Add text above the main document title.
- `\promotors{Name(s)}`: List the promotor(s) or supervisors for the document.

Typography and Graphics Commands:
- `\vubfont{Text}`: Typeset text in the official VUB font (TeX Gyre Adventor).
- `\vubfontbf{Text}`: Typeset text in the bold official VUB font.
- `\vubtriangle`: Manually insert the official orange VUB triangle (it is already automatically included on `\maketitle`).

### 2. Edit Section Files

Write your content in the separate section files:

- **`sections/01-introduction.tex`**: Introduction, background, research questions
- **`sections/02-methods.tex`**: Methodology, data, analysis
- **`sections/03-results.tex`**: Findings, figures, tables
- **`sections/04-discussion.tex`**: Interpretation, limitations, implications
- **`sections/05-conclusion.tex`**: Summary, contributions, future work

These files are automatically included in `main.tex` via:
```latex
\input{sections/01-introduction}
\input{sections/02-methods}
% ... etc
```
If you want to add more sections, simply create a new `.tex` file in the `sections/` folder and include it in `main.tex` as shown above.

### 3. Add References

To manage your bibliography, you can use the `bib/main.bib` file. This is a **BibTeX file** where you can add all your references in the standard BibTeX format. Each entry should have a unique citation key that you will use to cite it in your document. Below, I explain **how to automate this process using Zotero** and the **Better BibTeX plugin** (so when you add a reference to zotero this is automatically updated in the `bib/main.bib` file and can be used directly in your LaTeX document), but here is an example of how to add a reference manually:

```bibtex
@article{author2025,
    title={Article Title},
    author={Last, First and Second, Author},
    journal={Journal Name},
    year={2025},
    volume={10},
    pages={123--145}
}
```

Cite in your text:
```latex
As shown by \cite{author2025}...
Or: \citeA{author2025} demonstrated that...
```

### 4. Automating Your Bibliography with Zotero + Better BibTeX

[Zotero](https://www.zotero.org/) can automatically manage your `.bib` file so you never have to write BibTeX entries by hand, the same method can also be applied when you're using another Latex editor, just make sure to set the export path to your `bib/main.bib` file and enable auto-export. Below are the steps to set this up:

#### Install Zotero and Better BibTeX

1. Download and install [Zotero](https://www.zotero.org/download/).
2. Install the [Better BibTeX for Zotero](https://retorque.re/zotero-better-bibtex/installation/) plugin — this adds automatic BibTeX/BibLaTeX export and automatic generation of citation keys.
3. Go to Zotero's **Tools → Plugins**, click on the settings icon and **Install from file**, select the downloaded plugin file.
4. Restart Zotero after installing the plugin and make sure the plugin is enabled.

#### Collect References

Add references to your Zotero library using any of these methods:
- **Browser Connector**: Install the [Zotero Connector](https://www.zotero.org/download/) browser extension, then click the icon on any journal page, Google Scholar result, or arXiv page to save it instantly.
- **DOI/ISBN**: In Zotero, click the magic wand icon and paste a DOI or ISBN — metadata is fetched automatically.
- **Manual entry**: Add items by hand if needed.

#### Set Up Auto-Export to Your `.bib` File

1. In Zotero, select the collection (folder) you want to export, or select your entire library.
2. Go to **File → Export Library...** (or right-click a collection → **Export Collection...**).
3. Choose **Better BibTeX** as the format.
4. Check **Keep updated** — this enables auto-export so any new references you add are automatically written to the file.
5. Save to `bib/main.bib` in your **LaTeX project folder**.

Now, every time you add or edit a reference in Zotero, it will automatically update `bib/main.bib`. No manual copying needed.

#### Cite in Your Document

Use the citation key generated by Better BibTeX (visible in Zotero's "Citation Key" column):

```latex
As demonstrated by \cite{desmet2020}...
```

With the Zotero LaTeX VS Code extension installed, you can also press `Alt+Z` to search your Zotero library and insert a citation key directly (**This seems to be broken, i will look at it soon!**).


### 5. Building Your Document
When you are ready to compile your document and generate the PDF, you can do this directly in VS Code or via the command line.

#### VS Code (Recommended)
1. Open `main.tex` in VS Code
2. Press **`Ctrl+Alt+B`** or click the green **▶** button
3. PDF opens automatically in VS Code

#### Using the Command Line

```bash
# Full build with bibliography
latexmk -pdf -interaction=nonstopmode -outdir=build main.tex

# Clean build artifacts
latexmk -C -outdir=build

# Continuous preview (recompiles on save)
latexmk -pdf -pvc -interaction=nonstopmode -outdir=build main.tex
```


## VUB Styling

This template includes VUB official branding, provided by the [`texlive-vub`](https://gitlab.com/rubdos/texlive-vub) package created and maintained by **Ruben De Smet**.

The VUB LaTeX style files (`vub.sty`, `vubprivate.sty`, etc.) are licensed under the [LaTeX Project Public License (LPPL)](http://www.latex-project.org/lppl.txt), version 1.3 or later. The VUB logo is not covered by this license; you must obtain your own license for it.

Following are some of the key features of the VUB styling included in this template:

### Colors

```latex
\textcolor{vubbleu}{Blue text}      % VUB blue (CMYK: 1,.8,.16,.03)
\textcolor{vuboranje}{Orange text}  % VUB orange (CMYK: 0,.78,1.,0)
```

### Fonts

The template uses **TeX Gyre Adventor** (similar to Avenir), the official VUB font. It works automatically with both pdfLaTeX and XeLaTeX/LuaLaTeX.

### Logo and Triangle

The VUB logo and orange triangle are automatically added to the title page via `\maketitle`.


## LaTeX Quick Reference
This is a quick reference for common LaTeX commands and environments that you can use in your document. For more detailed information, check out the [Additional Resources](#additional-resources) section below.

### Document Structure

```latex
\section{Title}              % Main section
\subsection{Subtitle}        % Subsection
\subsubsection{Detail}       % Sub-subsection
```

### Figures

```latex
\begin{figure}[h]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/image.png}
    \caption{Your caption here}
    \label{fig:mylabel}
\end{figure}

% Reference it:
As shown in Figure~\ref{fig:mylabel}...
```

### Tables

```latex
\begin{table}[h]
    \centering
    \caption{Table caption}
    \label{tab:data}
    \begin{tabular}{|l|c|r|}
        \hline
        Column 1 & Column 2 & Column 3 \\
        \hline
        Data 1 & Data 2 & Data 3 \\
        \hline
    \end{tabular}
\end{table}

% Reference it:
See Table~\ref{tab:data} for details.
```

### Math

```latex
% Inline math
The equation $E = mc^2$ is famous.

% Display math
\begin{equation}
    \int_0^\infty e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
\end{equation}
```

### Lists

```latex
% Bulleted list
\begin{itemize}
    \item First item
    \item Second item
\end{itemize}

% Numbered list
\begin{enumerate}
    \item First step
    \item Second step
\end{enumerate}
```

### Citations

```latex
\cite{key}                   % (Author, Year)
\citeA{key}                  % Author (Year)
\citeyear{key}              % Year only
```


## Troubleshooting

### Common Issues

**Problem**: `File 'vub.sty' not found`
- **Solution**: Ensure the path `../archive/Latex/texlive-vub-v3.0.1/vub` exists, or update the path in `main.tex` line 11

**Problem**: `perl: command not found`
- **Solution**: Install [Strawberry Perl](http://strawberryperl.com/) and restart your terminal

**Problem**: Undefined references
- **Solution**: Compile twice. LaTeX needs two passes to resolve cross-references

**Problem**: Bibliography not showing
- **Solution**: Ensure you have at least one `\cite{}` command in your document

**Problem**: Fonts look wrong
- **Solution**: Install TeX Gyre Adventor fonts or they'll fall back to Computer Modern


## Additional Resources

### LaTeX Tutorials
- [Overleaf Documentation](https://www.overleaf.com/learn)
- [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX)
- [The Not So Short Introduction to LaTeX](https://tobi.oetiker.ch/lshort/lshort.pdf)

### Bibliography Management
- [Google Scholar](https://scholar.google.com/) - Export BibTeX citations
- [JabRef](https://www.jabref.org/) - Reference management software
- [Zotero](https://www.zotero.org/) - Bibliography manager (see Zotero guide above)



## License

This template is licensed under the [MIT License](LICENSE).

The VUB styling files (under `styles/`) are by [Ruben De Smet](https://gitlab.com/rubdos/texlive-vub) and licensed under the [LaTeX Project Public License (LPPL)](http://www.latex-project.org/lppl.txt), version 1.3 or later.


## Acknowledgments

- [Ruben De Smet](https://gitlab.com/rubdos/texlive-vub) for creating and maintaining the VUB LaTeX style package (`texlive-vub`), which this template is based on.

---

