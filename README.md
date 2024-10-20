# QuickNLPFreqTool

**Dependencies:** `scikit-learn, regex, spacy, matplotlib`.

**QuickNLPFreqTool** is a Python script designed for quick analysis of data samples using NLP tools.

In addition to the standard Python libraries, the software utilizes:

1. The built-in `collections` library with the Counter tool, which performs the technical task of counting word or word combination frequencies.

2. The built-in `sys` library for controlling the script's execution. Specifically, this library handles the termination of the software process.

3. The `regex` library for using regular expressions. Regular expressions allow for the cleaning of text from non-Cyrillic characters (which may be relevant for Russian texts containing links to online resources), end-of-line characters, carriage returns, and multiple space characters (this significantly cleans up the script’s output). The `regex` library is used as an alternative to the traditional `re` library to leverage the *Unicode Extended Latin* character category, which preserves the extended Latin character set in the English version. Comments have been left in the code to indicate how to revert to using `re`.

4. The `spaCy` library for semantic text analysis, enabling the selection of linguistic models for Russian and English languages (Large version) or the option to specify a custom model. This library is used for tokenizing and normalizing Russian words to ensure that, for example, "призрак" (ghost) and "призрака" (of the ghost) are not treated as two different results in the sample, allowing for subsequent filtering of function words (which can "clutter" the sample). spaCy is also used to find the vector of a word within the model, allowing for the calculation of word "similarity" in one of the modes, which is used for graphical representation of results.

5. The `scikit-learn` and `matplotlib` libraries for converting 300-dimensional vectors to two-dimensional space and subsequently displaying them on a flat plane. Essentially, this provides a visual representation of the linguistic similarity of words from the obtained sample.

There are **three modes** of operation:

- `words`: Simple counting of word frequencies. This mode is somewhat basic, but one of the most effective.

- `combos`: Counting the frequency of sequences of a specified length through simple enumeration. Practice shows that the peak efficiency of this mode is for sequences of 2-3 words.

- `vectors`: Counting the level of similarity between words from the original sample and a word specified by the user. Filtering options are available. For the first and third modes, there is an option to present results as a two-dimensional vector graph.

To achieve the best results, it is essential to compare all outputs of this software, for which an option to output to a file is available. Since the software accepts an input file in plain text format encoded in Unicode, the output will be similar, with no additional encoding taking place. The software is released under the Apache Version 2.0 license and is available on GitHub in an open-access format.

The script does not have a separate help page or any other launch keys. All nuances, options, and input requests are specified within the script itself or reflected in comments in the code. Please note that the script has been written by a **non-professional programmer**, and may even be from someone without programming experience.

## Version history (some outside the repository)

0.8.1 (October 2024) — A multitude of comments on various issues related to the script's operation has been added to the code.

0.8.0 (October 2024) — Official release of the script timed with the submission of research for journal editing.

0.7.3 (October 2024) — A function for dynamic translation of output using the MyMemory online service has been added and commented out.

0.7.2 (October 2024) — A function for drawing a graphical representation of word vectors for each mode has been added.

0.7.1 (October 2024) — The `spaCy` semantic mode has been removed due to unstable output. Overall, there are three modes: word frequency, word combination frequency, and the similarity level between the word entered by the user and words in the text.

0.7.0 (October 2024) — Removed `Gensim` and the custom word vector model in favor of the `spaCy` word vector model. The corresponding mode has been rewritten.

0.6.1 (October 2024) — Changed the formatting of status messages and user prompts.

0.6.0 (October 2024) — Another release version. Debugging of the code.

0.5.5 (October 2024) — Added two sampling filters: by the number of matches and by the level of similarity.

0.5.4 (October 2024) — Completed work on the fourth user mode. It calculates the similarity level between the word entered by the user and other words in the text. The functionality has been tested on both Russian and English texts.

0.5.3 (October 2024) — Transitioned from the re library to the regex library to support the `\p{Latin}` group for filtering extended Latin characters. An optional regular expression `[a-zA-Z]` has been added to limit to standard Latin characters.

0.5.2 (October 2024) — Filtering for the letter ё has been modified to account for the rare case when ё is written as e with a diaeresis.

0.5.1 (October 2024) — The available Russian vector model uses part-of-speech tags for each word (for an unknown reason). A feature has been included to add such tags. For simplicity, the tags `NOUN, ADJ, VERB, and ADV` are used.

0.5.0 (October 2024) — A fourth mode has been added, which computes the similarity of vector words. It works on test text, but produces errors on more complex samples. The number of libraries used has been changed.

0.4.3 (October 2024) — Text filtering has been changed to use a regular expression. It is now possible to exclude everything from the text except for Cyrillic, basic Latin or extended Latin characters.

0.4.2 (October 2024) — The function call to `spaCy` has been fixed. A missing option for filtering numbers has been added.

0.4.1 (October 2024) — Comments have been added.

0.4.0 (October 2024) — The second version of the script release. Moved away from NLTK in favor of the built-in `collections.Counter` to reduce the number of dependencies. Currently, the only additional dependency is `spaCy`, which requires downloading a linguistic model (the script specifies options for both English and Russian languages).

0.3.2 (October 2024) — The regular expression for text preparation has been edited considering `spaCy`'s capabilities (`spaCy` handles filtering of numbers and punctuation more effectively).

0.3.1 (October 2024) — English language support added through user dialogue with the choice of `spaCy` linguistic model.

0.3.0 (October 2024) — The code has been completely rewritten to leverage `spaCy`'s capabilities. Now, normalization and tokenization of words are done with this library.

0.2.1 (September 2024) — Extraction of the file-saving option into a separate function.

0.2.0 (September 2024) — Abandoning `PyMystem` in favor of `spaCy`. The semantic mode has been rewritten accordingly.

0.1.1 (September 2024) — The code has been proofread, and variables have been given clear names.

0.1.0 (September 2024) — The first release version of the script. All three user modes are operational, and dialogues are present for each scenario.

0.0.4 (September 2024) — Code quality improved; the first two user modes brought to a working version.

0.0.3 (September 2024) — User dialogues added.

0.0.2 (September 2024) — Functions introduced to improve code quality and enhance its modularity for future changes.

0.0.1 (April 2024) — The first version of the script. Uses `PyMorhy`, `PyMystem`, and `NLTK` for semantic analysis and word counting. There are significant limitations (the script needs to be manually edited for any changes in its operation). The first trial of the script has been conducted.
