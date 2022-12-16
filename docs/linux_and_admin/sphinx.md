# Sphinx 

## Introduction 

Sphinx makes it easy to create intelligent and beautiful documentation.

For more information visit site [here](https://www.sphinx-doc.org/en/master/index.html#).

---
## Table of content

[1. Installation](#1-ubuntu-installation-overhead)

[2. Setting up Sphinx Documentation](#2-setting-up-documentation)

[3. Sphinx Themes](#3-additional-steps-sphinx-themes)

---
## 1. Installation Overhead

Instal necessary files sphinx  & make 
```bash
sudo apt-get install python3-sphinx
sudo apt-get install -y make 
```

---
## 2. Setting up documentation 

**Step 1:** Create new directory for documentation
```bash
mkdir docs
cd docs
```

**Step 2:** Run sphinx quickstart

Choose separate source from build. (Places .html and .rst files in different folders)
```bash
sphinx-quickstart
```

**Step 3:** Edit conf.py file to allow Sphinx to find folder path

In ```conf.py``` file:

1.  Uncomment out and change the following lines
    ```bash
    import os
    import sys
    sys.path.insert(0, os.path.abspath(os.path.join('..', '..', 'src')))
    ```
2. Add the following extensions ```extensions = ['sphinx.ext.autodoc', 'sphinx.ext.napoleon']```

**Step 4:** Use sphinx API doc to create html file

Create API doc and 
```bash
sphinx-apidoc -o ./source ../src
make html
```

**Step 5:** View html

Navigate to folder and open index.html file
```bash
open build/html/index.html
```

## 3. Additional Steps: Sphinx Themes
---

To view available themes use this link: [Browse Sphinx themes](https://sphinx-themes.org)

### Installation Steps:

**Step 1:** Install theme
```bash
pip install sphinx-press-theme
```
**Step 2:** Edit Conf.py file
```bash
html_theme = 'press'
```
**Step 3:** Refresh and rerun with new theme

delete rst files that are outdated and repeat steps 4 of [documentation](#2-setting-up-documentation)
