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
