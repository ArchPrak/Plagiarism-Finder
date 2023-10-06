# Plagiarism-Finder
A prototype model for a plagiarism detection tool built using Metaphor APIs

## Context
This tool can be used to assist grading academic projects by detecting plagiarised content. Given the link to a Github Rpository of a project, this tool identifies similar dcouments that can be found on the internet. 
It generates a report mentioning the top 10 most similar pages and generates a report containing this information. This report can be used during grader to understand how original the project work is. 

## Implementation Details
This tool has been built using [Metaphor](https://docs.metaphor.systems/reference/getting-started-1) APIs. 
Given an input as the project Github URL, the tool performs the following steps: 
1. Using the Metaphor Find Similar Links API, it finds the top 10 pages that are most similar to this repository.
2. Using the Metaphor get document content API, it fetches the HTML content from the most similar page.
3. Using NLP libraries, the above content of the page is parsed and summarized to finally generate a search query for this content.
4. Using the generated search query, the Metaphor Search API is queried to find additional relevant documents that might have not been identified with the similar links API used in step 1.
   This is particularly required to identify other sources of code.

## Future Enhancements
This project was built solely out of interest and with an aim to explore the Metpahor APIs and their potential. This tool is still in a preliminary stage and can be enhanced in many ways to be efficiently used:
1. Adding similiarity/ plagiarism scores to the report to quantify the results.
2. Better support for code similarity detection. Currently it works best for texts (although it does pickup information from README files of github repos)

## Set up
Install the required package with 
`pip install metaphor-python`

Download the .ipynb/.py file, open it on Jupyter notebook or Google collab and execute the file. 
Input: URL to the project being graded (for eg a github link)
Output: Plagiarism report

## References: 
https://docs.metaphor.systems/reference/getting-started-1

