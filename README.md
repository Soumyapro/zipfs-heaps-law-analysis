# Zipf's and Heap's Law Analysis

A short project verifying two well known statistical laws of natural language, Zipf's Law and Heap's Law, using the text of *Alice's Adventures in Wonderland* by Lewis Carroll.

## What this project does

1. Fetches the full text of *Alice's Adventures in Wonderland* directly from Project Gutenberg using `requests`.
2. Cleans the text by removing Gutenberg's header and footer boilerplate.
3. Tokenizes the text into words using regex, handling punctuation, em dashes, and apostrophes (both straight and curly).
4. Verifies **Zipf's Law**: checks whether word frequency is inversely proportional to word rank.
5. Verifies **Heap's Law**: checks whether vocabulary size grows as a power of total word count.
6. Fits both relationships using log log linear regression and reports the exponents and R² values.

## Results

### Zipf's Law
Word frequency plotted against rank on a log log scale.

![Zipf's Law plot](zipf_law.png)

- Exponent (s): **≈ 0.85**
- R²: **≈ 0.99**

The plot shows a strong linear relationship in the higher ranked words. The tail shows a staircase pattern caused by hapax legomena, words that appear only once, which share identical frequency values. Trimming the data to the top ranks before fitting gave a cleaner, more reliable slope.

### Heap's Law
Vocabulary size (unique words) plotted against total words read, on a log log scale.

![Heap's Law plot](heap_law.png)

- Exponent (β): **≈ 0.64**
- R²: **≈ 0.98**

This is slightly higher than the typical 0.4 to 0.6 range reported for natural language, likely due to the book's short length and its unusually inventive, nonsense heavy vocabulary.

## Key takeaways

- Both laws hold reasonably well for this text, with high R² values confirming strong linear fits.
- Exact exponents deviate somewhat from textbook values, which is expected for a short, single genre text.
- Real text tokenization has real quirks (curly quotes, em dashes, contractions) that need careful handling before any statistical analysis is meaningful.

## Tech stack

- Python
- `requests` for fetching text data
- `re` and `collections.Counter` for tokenization and frequency counting
- `numpy` and `scipy.stats` for log transforms and linear regression
- `matplotlib` for plotting

## Future work

- Compare exponents across different text types, such as formal or technical writing versus informal or conversational text, to see how genre affects these laws.
- Test on longer corpora to see if exponents converge closer to textbook values.

## Files

- `zipf_heaps_law_alice_in_wonderland.ipynb`: full analysis notebook
- `zipfs_law.png`: Zipf's Law plot
- `heaps_law.png`: Heap's Law plot
