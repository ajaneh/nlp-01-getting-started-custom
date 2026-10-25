# Comparing word frequency from different political parties

Web Mining and Applied NLP | Project 01 | Alex Heyert | 10-2026

## Overview

This project adapts a single-page web-text example into a small comparison of
the 2024 Democratic and Republican party platforms. The
[notebook](https://github.com/ajaneh/nlp-01-getting-started-custom/blob/main/notebooks/web_words_heyert.ipynb) retrieves both documents,
processes their text in parallel, and visualizes frequently used words.

## Custom Project

- Replaced the example webpage with the 2024 Republican and Democratic party
  platform pages.
- Applied the same retrieval, text extraction, and analysis steps to both
  pages, keeping each result labeled by party.
- Added separate word clouds and a bar chart comparison of the most frequent
  words.

## Data

The notebook retrieves the platform pages from
[The American Presidency Project](https://www.presidency.ucsb.edu/):

- [2024 Republican Party Platform](https://www.presidency.ucsb.edu/documents/2024-republican-party-platform)
- [2024 Democratic Party Platform](https://www.presidency.ucsb.edu/documents/2024-democratic-party-platform)

The pages are fetched when the notebook runs; no separate local text dataset
is used. The fetched page content may change if the source website changes.

## Method

The notebook applies the following workflow to each page:

1. **Retrieve the pages.** Requests downloads each URL with a user agent
   header and a timeout. The notebook prints the HTTP response status and
   raises an error for unsuccessful responses.
2. **Extract text.** BeautifulSoup parses the HTML and python normal library combines
   text with spaces and strips surrounding whitespace.
3. **Clean tokens.** Text is split into words and lowercased. A custom set of
   stop words removes common words and selected filler terms. Words of four
   characters or fewer are excluded.
4. **Count words.** Polars dataframes make the words easy to use and group.
5. **Visualize.** Matplotlib displays the ten most frequent words for each
   platform side by side. WordCloud creates a separate word cloud from each
   platform's frequency table.

## Results and Interpretation

The visualizations offer an exploratory view of vocabulary in the two
documents:

![Republican platform word cloud](images/r_word_cloud.png)

![Democratic platform word cloud](images/d_word_cloud.png)

![Comparison of frequent words](images/comparison_bar_chart.png)

These are counts of cleaned words, not a measure of the importance or meaning
of a policy. The cleaning choices affect which words appear and how often.
Also the notebook extracts text from the full HTML page rather than selecting
only the platform's article body, so page navigation or other surrounding
elements may influence the counts. The democratic speech contained almost 3 times as many characters

## Reproduce the Analysis

Open and run the
[project notebook](https://github.com/ajaneh/nlp-01-getting-started-custom/blob/main/notebooks/web_words_heyert.ipynb).

## Documentation Index

- [Project Instructions](project-instructions.md)
- [Glossary](glossary.md)

## Project Links

- [GitHub Repository](https://github.com/ajaneh/nlp-01-getting-started-custom)
- [Project Notebook](https://github.com/ajaneh/nlp-01-getting-started-custom/blob/main/notebooks/web_words_heyert.ipynb)
- [Professional Python Guide](https://denisecase.github.io/pro-analytics-02/)
- [Professional Python Project Explainer](https://pup-pack.github.io/professional-python-project-explainer/)
