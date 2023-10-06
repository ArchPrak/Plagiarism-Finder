# Plagiarism-Finder
A prototype model for a plagiarism detection tool built using Metaphor APIs

## Context
This tool can be used to assist in the grading of academic projects by detecting plagiarized content. Given the link to a Github Repository of a project, this tool identifies similar content that can be found on the internet. It generates a report mentioning the top 10 most similar pages and generates a report containing this information. This report can be used to assist grading to understand how original the project work is.

## Implementation Details
This tool has been built using [Metaphor](https://docs.metaphor.systems/reference/getting-started-1) APIs. 
Given an input as the project Github URL, the tool performs the following steps: 
1. Using the [Metaphor Find Similar Links API](https://dashboard.metaphor.systems/playground/find-similar), it finds the top 10 pages that are most similar to this repository.
2. Further, using the [Metaphor get document content API](https://dashboard.metaphor.systems/playground/get-contents), it fetches the HTML content from the most similar page.
3. Using NLP libraries, the above content of the page is parsed and summarized to finally generate a search query for this content.
4. Using the generated search query, the [Metaphor Search API](https://dashboard.metaphor.systems/playground/search) is queried to find additional relevant documents that might have not been identified with the similar links API used in step 1. This step was particularly incorporated for the below reasons: 

   a. To combine the capabilities of both search and similar links api in generating  an exhaustive report

   b. To identify any pages missed by the similar links API.  It was observed that the similar links API did not perform well when given links to code files. (i.e., similarity based on code is not currently supported) Hence, as a humble attempt, this tool tries to support this feature by retrieving the content of a README file, and then parsing it to understand the content and create a search query of the format: ‘Code for <project summary>’. This helps identify other code sources that might have been missed by the similar links API.

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

