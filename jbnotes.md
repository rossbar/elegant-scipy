# General setup
 - Extra installs (added to requirements.txt):
   * jupyter-book
   * jupytext

 - Create a new book: `jb create jupybook`

## Text version of jupyter notebooks (myst)

According to the [myst-nb docs][myst-nb], it is possible to convert existing
notebooks into a text-based format with `jupytext`.

 - Use the existing `elegant-scipy` build tools (i.e. `notedown`) to convert
   the markdown source to notebooks *without* running them. The simplest way
   to do this is to modify the Makefile to suppress the `--run` flag then:
   ```bash
   make all
   ```
   This creates the (un-executed) notebooks in the `ipynb/` directory

 - **NOTE:** To test text-based notebook format: convert to myst-nb format with
   `jupytext`:
   ```bash
   cd ipynb/
   jupytext -k python3 *.ipynb --to myst
   ```
   This creates *.md files in myst-nb format for each of the notebooks

   * NOTE: `jupyter-book` won't work with the preface.md converted to myst-nb
     format - it must by .md format to keep things from borking (as of
     jb 0.7)

 - Copy the source files (either *.md **or** *.ipynb) to `jupybook`
 - Modify `_toc.yml`: remove template files and add all new source files
   * Make sure not to include file extensions in `_toc.yml`

 - **MISC STEP** - Add links to `data/` and `style/` dirs, e.g.
   * `ln -s data ../data`
   * `ln -s style ../style`
   * `ln -s images ../images`
   TODO: Figure out how to automate this within jupyter-book

 - Build the book: `jb build .`

[myst-nb]: https://myst-nb.readthedocs.io/en/latest/use/markdown.html

# General notes and issues

 - [ ] TOC doesn't yet seem to be figured out
   - including a {toctree} directive in a file causes doubling of the toc in 
     the nav bar
