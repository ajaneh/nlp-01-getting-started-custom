
# nlp-01-getting-started-custom

[![Python 3.14](https://img.shields.io/badge/python-3.14%2B-blue?logo=python)](pyproject.toml)
[![CI](https://github.com/ajaneh/nlp-01-getting-started-custom/actions/workflows/ci-python-zensical.yml/badge.svg)](https://github.com/ajaneh/nlp-01-getting-started-custom/actions/workflows/ci-python-zensical.yml)
[![Documentation](https://img.shields.io/badge/docs-site-blue?logo=github)](https://ajaneh.github.io/nlp-01-getting-started-custom/)

[![uv managed](https://img.shields.io/badge/uv-managed-DE5FE9)](https://docs.astral.sh/uv/)
[![ty type checked](https://img.shields.io/badge/ty-type_checked-2F80ED)](https://docs.astral.sh/ty/)
[![Zensical docs](https://img.shields.io/badge/Zensical-docs-purple)](https://zensical.org/)
[![MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE)

> Retrieve, process, and visualize text from the web using Python.

## Project Overview

Author: Alex Heyert

Date: 2026 October

This is my customized first project for the Web Mining and Applied NLP course.
It explores word frequencies in the 2024 Democratic and Republican party
platforms, rather than analyzing a single example webpage.

## Data

The notebook retrieves the platform pages directly from
[The American Presidency Project](https://www.presidency.ucsb.edu/):

- [2024 Republican Party Platform](https://www.presidency.ucsb.edu/documents/2024-republican-party-platform)
- [2024 Democratic Party Platform](https://www.presidency.ucsb.edu/documents/2024-democratic-party-platform)

## Custom Project

I adapted the project to compare two related documents and added visual
summaries for each platform, along with a chart for comparing frequent words.

## Results

The analysis produces a word cloud for each platform and a bar chart comparing
frequent words. These visualizations provide an exploratory view of the words
used in the two documents.

### Project Visualization

![Republican word cloud](docs/images/r_word_cloud.png)
![Democratic word cloud](docs/images/d_word_cloud.png)
![Comparison of frequent words](docs/images/comparison_bar_chart.png)

## Developer Steps

### Initialize and Update the Python Environment

With the project open in VS Code, open a VS Code terminal.

```shell
uvx pup-clean --delete
uv self update
uv python pin 3.14
uv python install
uv lock --upgrade
uv add --dev prek
uv sync
uv audit

#Git hooks
git add -A
uv run prek run --all-files
# repeat if changes were made
uv run prek run --all-files

#Clean up
uv run ruff check . --fix
uv run ruff format .

uv run ty check
uv run python -m pytest
uv run python -m zensical build

#Commit
git add -A
git commit -m "describe your changes in quotes"
git push -u origin main
```

### Run the Notebook

Go to the [Notebook](notebooks/web_words_heyert.ipynb), select kernel, run all.

## Links

- [Hosted Documentation](https://ajaneh.github.io/nlp-01-getting-started-custom/)
- [Example Project](https://github.com/denisecase/nlp-01-getting-started)
- [Data Source](https://www.presidency.ucsb.edu/)
- [Professional Python Workflow Guide](https://denisecase.github.io/pro-analytics-02/)
- [Citation](CITATION.cff)
- [License](LICENSE)
