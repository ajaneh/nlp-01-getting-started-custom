# Comparing Word Frequencies in the 2024 Party Platforms

**Author:** Alex Heyert

**Project:** Web Mining and Applied NLP | Project 01

**Date:** 2026-10

This project compares word frequencies in the 2024 Democratic and Republican
party platforms. It retrieves both pages, extracts and cleans their text, and
visualizes frequent words. The analysis is exploratory; word counts do not
explain the context or meaning of a policy.

## Data

The data comes from The American Presidency Project:

- [2024 Republican Party Platform](https://www.presidency.ucsb.edu/documents/2024-republican-party-platform)
- [2024 Democratic Party Platform](https://www.presidency.ucsb.edu/documents/2024-democratic-party-platform)

The notebook retrieves the pages when it runs and no separate local text dataset
is used. The analysis compares two documents. Each
frequency table record represents a word in one platform and its observed
count after cleaning.

**Record grain:** one platform-document for the source text. one
platform-and-word pair in the frequency tables.

**Retrieved on:** Oct 25 2026

## Techniques Applied

The project adapts the starter example's web-text workflow in
[`notebooks/web_words_heyert.ipynb`](https://github.com/ajaneh/nlp-01-getting-started-custom/blob/main/notebooks/web_words_heyert.ipynb):

- **HTTP retrieval — Requests:** fetches both platform pages with a User-Agent
  header and timeout.
- **HTML parsing and text extraction — BeautifulSoup:** parses each page, then
  the native python library combines page text with spaces and strips surrounding whitespace.
- **Token cleaning — Python:** splits and lowercases text, removes selected
  stop words, excludes short tokens, and strips surrounding punctuation.
- **Frequency analysis — Polars:** groups tokens by word and counts each word
  separately for each platform.
- **Visualization — Matplotlib and WordCloud:** plots the ten most frequent
  words for each platform and creates a word cloud for each frequency table.

## Custom Modifications

The starter example analyzed one webpage. I changed the input to the 2024
Democratic and Republican party-platform pages and applied the same workflow
to both, keeping the two results separate. I added separate word clouds and a
bar chart comparison.

- **Why I made this change:** I wanted to increase the complexity without adding new tools.
- **Observed effect:** Despite adjusting which filler words to exclude a few times, some non specific words were common. When looking at the ranked bar chart comparing the top 20 frequencies it's interesting to see that "american" is the first most frequent word in the Republican platform but the 20th ranked on the Democratic platform.

## Methods and Settings

- Both URLs are retrieved in a loop the notebook prints the HTTP status and
  raises an error when a response is unsuccessful.
- BeautifulSoup parses the full HTML page. Text is extracted with spaces
  between chunks and surrounding whitespace stripped.
- Words are lowercased and split on whitespace. A custom stop-word set
  removes common words and selected filler terms. A word must have more than
  three characters.
- Polars counts occurrences of each cleaned word separately for each
  platform.
- The comparison chart shows the ten most frequent words per platform.

**Stop-word choices:** When I searched for ways to filter out common words I saw I could add another tool, or grab an advised list. I chose to use the advised list and added a few words that seemed excessive. For example the democratic party said president at least twice as many times because the phrases where it appeared were typically "President Biden, and Vice President Harris".

## Verification

- The saved notebook output reports HTTP 200 for both source pages.
- The Zensical documentation build completed successfully during the report
  update.
- Notebook run: Is succesful
- I didn't create or add custom tests, just print statements along the way to sanity check the work.

## Results

The notebook includes a two word clouds which give a visual overview of the difference in language used.

![Republican platform word cloud](https://github.com/ajaneh/nlp-01-getting-started-custom/blob/main/docs/images/r_word_cloud.png?raw=true)

![Democratic platform word cloud](https://github.com/ajaneh/nlp-01-getting-started-custom/blob/main/docs/images/d_word_cloud.png?raw=true)

![Comparison of frequent words](https://github.com/ajaneh/nlp-01-getting-started-custom/blob/main/docs/images/comparison_bar_chart.png?raw=true)

**Numeric results:**
Sample of republican word frequencies:
american: 79
republicans: 71
america: 28
restore: 25
people: 23
republican: 22
protect: 22
education: 21
party: 21
great: 20

Sample of democratic word frequencies:
Sample of word frequencies (Democratic speech):
biden: 242
more: 231
democrats: 201
care: 166
health: 164
administration: 152
people: 146
american: 142
than: 123
families: 122

## Observations

Record what is visible in the outputs without explaining why it occurred:

- Each parties name appears frequently.
- The democratic party's former president appears often "Biden", but not the republican presidential Nominee "Trump"

## Interpretation and Insights

This is a preliminary comparison so I don't want to imply and significant insights, what is clear from the word clouds, is that the choice of language is different between the two parties.

## Limitations

- The notebook extracts text from the full webpage rather than selecting only
  the platform article body, so navigation and other page content may affect
  counts.
- Stop-word selection and the minimum token length influence which words
  remain in the analysis.
- Raw word counts can be affected by differences in document length they are
  not normalized rates.
- The analysis covers only these two platform pages, and live page content may
  change at the source (although the APP is considered reliably static).
- Word frequencies do not capture context, sentiment, policy importance, or
  the meaning of phrases.

## Next Steps

It would be interesting to use something like AWS sentiment analysis to determine the emotional tone.
