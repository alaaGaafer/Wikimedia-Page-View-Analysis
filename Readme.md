# Wikimedia Page View Analysis

## Project Overview

This project involves analyzing page view statistics for Wikimedia projects. The data consists of page views generated between 0-1 am on January 1, 2016. Each line in the dataset contains the following fields:
- Project code: The project identifier for each page.
- Page title: A string containing the title of the page.
- Page hits: The number of requests on the specific hour.
- Page size: The size of the page.

The objective is to implement various queries using Apache Spark's map-reduce paradigm and Spark loops, then compare their performance in terms of time.

## Data Preparation

1. **Data Loading**: The dataset is loaded into Spark for processing.
2. **Data Parsing**: Each line of the dataset is parsed to extract relevant fields for analysis.

## Queries Implemented

### Query 1: Page Size Statistics

- **Objective**: Compute the minimum, maximum, and average page size.
- **Map-Reduce Paradigm**:
  - Parse the data to extract page sizes.
  - Use custom `reduce` functions to find the minimum and maximum page sizes.
  - Compute the total page size and count the number of entries to calculate the average.
- **Spark Loops**:
  - Iterate over the parsed data to calculate the minimum, maximum, and total page size.
  - Compute the average page size.

### Query 2: Page Titles Starting with "The"

- **Objective**: Determine the number of page titles that start with the article "The". Additionally, find how many of those page titles are not part of the English project.
- **Map-Reduce Paradigm**:
  - Filter page titles that start with "The".
  - Count the number of such titles and those that are not part of the English project.
- **Spark Loops**:
  - Iterate over the parsed data to count page titles starting with "The" and identify non-English titles.

### Query 3: Unique Terms in Page Titles

- **Objective**: Determine the number of unique terms appearing in the page titles. Terms are delimited by underscores ("_") and are normalized by lowercasing and removing non-alphanumeric characters.
- **Map-Reduce Paradigm**:
  - Extract and normalize terms from page titles.
  - Count the number of unique terms.
- **Spark Loops**:
  - Iterate over the parsed data to extract and normalize terms.
  - Use a set to track unique terms.

### Query 4: Page Title Frequency

- **Objective**: Extract each title and the number of times it was repeated.
- **Map-Reduce Paradigm**:
  - Map each title to a (title, 1) pair.
  - Reduce by key to count the occurrences of each title.
- **Spark Loops**:
  - Iterate over the parsed data to count occurrences of each title using a dictionary.

### Query 5: Combine Pages with the Same Title

- **Objective**: Combine data of pages with the same title and save each pair of pages' data to display them.
- **Map-Reduce Paradigm**:
  - Parse pages and group by title.
  - Combine data for pages with the same title and prepare them for display.
- **Spark Loops**:
  - Iterate over the parsed data to group pages by title.
  - Combine data for pages with the same title and prepare them for display.

## Results and Performance Comparison

- **Query 1**:
  - Minimum, maximum, and average page sizes were computed.
  - Map-Reduce Paradigm and Spark Loops produced identical results.
- **Query 2**:
  - The number of titles starting with "The" and non-English titles were determined.
  - Both approaches yielded the same counts.
- **Query 3**:
  - The number of unique terms in page titles was calculated.
  - Consistent results were obtained from both methods.
- **Query 4**:
  - Page title frequencies were extracted.
  - Identical results were achieved using both paradigms.
- **Query 5**:
  - Pages with the same title were combined.
  - Both approaches provided the same combined data.

### Performance

- **Map-Reduce Paradigm**: Efficient for large datasets, leveraging distributed processing.
- **Spark Loops**: Straightforward but may not scale as efficiently as the map-reduce approach for very large datasets.

## Conclusion

Both map-reduce and Spark loops were effective in performing the required queries. The choice between the two approaches depends on the specific requirements and scale of the dataset. Map-reduce paradigms are generally more scalable and suitable for large-scale data processing.


