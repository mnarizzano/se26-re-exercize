## Functional Requirements Analysis

1. Dictionary

**Original:** The system allows the explanation of complicated words written by professional authors

**Problems:** "Complicated words" is highly subjective: what is complicated to one person is simple to another. "Written by professional authors" is confusing; does it mean the definitions are written by professionals, or the tool only works on books by professionals?

**Fixed Requirement:** The system shall provide a built-in dictionary interface that displays standard definitions for any word the user selects within the uploaded text.

2. Text to Voice

**Original:** The system should allow to transform the text into voice in all language just by pressing a bottom showed up the text

**Problems:** Supporting "all languages" is technically impossible. "Bottom" is a typo for button. "Showed up the text" is unclear UI design.

**Fixed Requirement:** The system shall include a text-to-speech function, activated via a user interface button, capable of reading the text aloud in at least English, Spanish, and French.

3. Repetition Detection

**Original:** The system shall analyze the text and detect repeated words and expressions by counting their frequency and identifying those above a defined threshold.

**Problems:** "A defined threshold" is ambiguous. Who defines it? The user? The developer?

**Fixed Requirement:** The system shall allow the user to input a numeric threshold (e.g., >5 occurrences per 1,000 words) and automatically highlight any words or exact phrases that exceed this limit.

4. Narrative Suggestions

**Original:** The system shall provide suggestions to improve narrative quality by analyzing detected issues and generating relevant recommendations.

**Problems:** "Improve narrative quality" and "relevant recommendations" are completely subjective.

**Fixed Requirement:** The system shall generate a list of actionable text-editing prompts (e.g., "Reduce passive voice instances by 10%") corresponding directly to the metrics that fall outside standard baseline ranges.

5. Grammar Issues

**Original:** The system shall detect grammar issues by using predefined grammar rules and language processing techniques.

**Problems:** Mentioning "language processing techniques" dictates how the developers should build it (implementation), not what the system should do.

**Fixed Requirement:** The system shall identify and highlight grammatical errors (such as subject-verb agreement and incorrect verb tense) based on a configurable, standard language ruleset.

6. Document Upload

**Original:** The system shall allow users to upload documents by supporting file formats such as PDF, TXT and DOCX.

**Problems:** "Such as" is open-ended. Requirements must be exhaustive.

**Fixed Requirement:** The system shall allow users to upload text documents exclusively in .PDF, .TXT, and .DOCX formats.

7. Dialogue-to-Description Ratio

**Original:** Dialogue-to-Description Ratio: A visual breakdown of "showing vs. telling" by measuring the balance of spoken text versus prose.

**Problems:** This is written as a feature description, not a "shall" statement and spoken text is not well defined.

**Fixed Requirement:** The system shall calculate and display a pie chart representing the percentage of total word count enclosed in quotation marks compared to the remaining unquoted text.

8. Readability Indexing

**Original:** Readability Indexing: Automated scoring to ensure the text matches the intended target audience's level.

**Problems:** It lacks a "shall" statement. Also, the system cannot "ensure" the text matches the audience; it can only score it.

**Fixed Requirement:** The system shall calculate and display a readability score for the uploaded manuscript.

9. Text Upload Methods

**Original:** The system should allow for user text upload, both as a "copy and paste" and .txt files (in case of big texts).

**Problems:** Contradicts requirement #6 (which allows PDF and DOCX). Justifications ("in case of big texts") is ambiguous. "Should" is weaker than "shall".

**Fixed Requirement:** The system shall allow users to input text either by pasting it directly into a designated text field (max 10.000 characters) or by uploading a supported file type.

10. Post-Upload Trigger

**Original:** After the upload the system should check the following functionalities.

**Problems:** This is an incomplete sentence and acts as a header rather than a testable requirement.

**Fixed Requirement:** Upon successful text input via upload or paste, the system shall automatically initiate the text analysis workflow without further user prompting.

## Non-Functional Requirements Analysis

11. Summary Format

**Original:** Summary Format: the summary generated should be at maximum 10 lines

**Problems:** "Lines" is an ambiguous metric for software. 

**Fixed Requirement:** The generated summary report shall not exceed 250 words.

12. Performance (Speed)

**Original:** The system shall generate the analysis report within 5 seconds for texts up to 50,000 words.

**Problems:** While perfectly formatted and testable, 5 seconds to run complex analysis on a 50,000 book is highly unrealistic from a technical standpoint (achievability risk).

**Fixed Requirement:** The system shall generate the analysis report within 60 seconds for manuscripts containing up to 50,000 words.

13. Reliability

**Original:** The system shall ensure reliability by completing at least 95% of analysis requests without errors.

**Problems:** A 95% success rate means 1 out of every 20 users experiences a crash. That is an unacceptably high failure rate for commercial software.

**Fixed Requirement:** The system shall maintain a 99.9% successful processing rate for valid file uploads, excluding errors caused by user-side network disconnections.

14. Compatibility

**Original:** The system shall ensure compatibility by supporting at least 3 file formats (e.g., PDF, DOCX, TXT) for input and output.

**Problems:** "At least 3" and "e.g." are ambiguous. Outputting a formatted report in .TXT would strip away all the visual charts. You need to separate input and output.

**Fixed Requirement:** The system shall support .PDF, .DOCX, and .TXT for manuscript input, and exclusively generate the final analysis reports in .PDF format.

15. Scalability

**Original:** The system must support up to 500 concurrent text analysis requests while continuing to meet the processing time defined in the Performance requirement.

**Problems:** Referencing another requirement loosely instead of stating the metric, which forces the reader to go hunting for the number.

**Fixed Requirement:** The system shall support up to 500 concurrent text analysis requests while maintaining a maximum processing time of 60 seconds per request.

16. Extensibility

**Original:** The system must utilize a modular architecture (e.g., via APIs or microservices) ensuring that new analytical metrics or language rulesets can be deployed independently without requiring recompilation of the core text-parsing engine.

**Problems:** Recommending APIs or microservices borders on architectural design rather than requirements engineering, but as a system constraint, it is generally acceptable. We can just tighten the wording.

**Fixed Requirement:** The system shall allow the deployment of new language rulesets or analytical modules without requiring a system restart or recompilation of the core application.