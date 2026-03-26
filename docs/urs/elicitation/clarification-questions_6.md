Functional Requirements

1. Multi-Format Text Upload
Definition: How does the system recognize and define "chapter breaks" across different file formats (e.g., looking for page breaks, specific heading styles, or the word "Chapter")?
Boundary: Is there a maximum file size (in MB) or maximum word count limit for a single manuscript upload?
Behavior: What should the system do if a user uploads a PDF that consists of scanned images rather than selectable text (e.g., throw an error, or attempt OCR)?

2. Repetition & Redundancy Tracker
Definition: What distinguishes an "unintended echo" from a deliberate repetition used for stylistic effect?
Boundary: What is the specific proximity threshold for a word to be flagged as repeated (e.g., within the same paragraph, same 500 words, same chapter)?
Behavior: Will the system automatically ignore common stop words (e.g., "the", "and", "a") or can the user customize an ignore list?

3. Dialogue-to-Description Ratio
Definition: How does the system define "dialogue" (e.g., relying strictly on standard quotation marks, and how does it handle em-dashes or single quotes used in other languages)?
Boundary: Will the system flag ratios that deviate from a specific baseline, or will it merely report the raw percentage?
Behavior: How should the system categorize internal monologues, which are often italicized rather than explicitly quoted?

4. Character Interaction Map
Definition: How does the system identify a "character" (e.g., capitalized names, NLP entity recognition) and how does it link pronouns or nicknames to the main entity?
Boundary: Is there a limit to the number of characters the map can display before the visual matrix becomes unreadable?
Behavior: How does the system define characters being "together" (e.g., mentioned in the same sentence, the same scene, or the same chapter)?

5. Pacing Heatmap
Definition: What specific mathematical metrics define a "slow" versus "rushed" section (e.g., words per sentence, syllables per paragraph)?
Boundary: At what level of granularity is the heatmap generated (e.g., sentence-by-sentence, paragraph-by-paragraph, or chapter-by-chapter)?
Behavior: How is the heatmap visually presented to the user (e.g., color-coded text highlighting, or a standalone bar chart)?

6. Lexical Variety Score
Definition: Does "unique vocabulary" account for stemming and lemmatization (e.g., counting "run", "ran", and "running" as one root word or three distinct words)?
Boundary: Is the score calculated against the entire manuscript as a whole, or averaged out chapter-by-chapter?
Behavior: Does the system compare the score against a baseline dataset of published works to determine the "sophistication" of the prose?

7. Readability Indexing
Definition: Which specific readability algorithms will be implemented (e.g., Flesch-Kincaid, Gunning Fog, SMOG)?
Boundary: Can the user manually set the "intended target audience's level" (e.g., Young Adult, Middle Grade, Adult) before running the analysis?
Behavior: What specific feedback or suggestions does the system provide if the text significantly deviates from the target audience level?

8. Sentiment/Tone Analysis
Definition: What specific emotional categories are being tracked (e.g., a simple positive/negative/neutral scale, or specific emotions like joy/anger/sadness)?
Boundary: How does the system handle sarcasm or irony, where the literal words might contradict the actual narrative tone?
Behavior: How is the "emotional arc" visualized over the timeline of the manuscript?

9. Cliché & Weak Verb Detection
Definition: Is the list of "tired metaphors" and "weak verbs" hardcoded, or does it update dynamically from an external database?
Boundary: Can the user customize the dictionary of clichés to whitelist certain phrases they use intentionally?
Behavior: Does the system actively suggest alternative strong verbs and fresh metaphors, or does it simply highlight the weak ones for the user to fix?

10. Automated Summary Report
Definition: What specific threshold or metric qualifies an issue as a "red flag warning" versus a standard observation?
Boundary: Is there a maximum length or page limit for the generated PDF dashboard?
Behavior: Can the user toggle specific metrics on or off to customize what is included in the final PDF report?

Non-Functional Requirements

11. Performance
Definition: What defines a "standard" manuscript formatting (e.g., plain text vs. a document heavy with custom fonts and tables)?
Boundary: Does the 360-second limit apply strictly under peak server load, or is it the baseline for normal conditions?
Behavior: What feedback is shown to the user while they wait for those 360 seconds (e.g., a progress bar, a loading animation, an email notification when done)?

12. Usability
Definition: How is a "first-time user" defined for QA testing purposes (e.g., specific tech literacy level, specific age demographic)?
Boundary: Does the 2-minute threshold include the time it takes for the file to physically upload over the user's internet connection?
Behavior: If a user fails to initiate the report within 2 minutes, what automated fallback guidance does the system provide (e.g., a pop-up tutorial)?

13. Security (Data Privacy)
Definition: Who holds and manages the encryption keys for the AES-256 encrypted files at rest (the cloud provider, the system administrators, or the user)?
Boundary: How long are the encrypted manuscripts retained on the server before being automatically and permanently deleted?
Behavior: What happens to the encryption status and file access if a user decides to delete their account?

14. Scalability
Definition: Does "concurrent text analysis requests" mean 500 uploads happening at the exact same millisecond, or 500 reports actively processing simultaneously?
Boundary: What is the exact behavior if request number 501 comes in (e.g., is it placed in a queue, or does it fail with an error message)?
Behavior: Does the system automatically provision more server resources (auto-scaling) dynamically to handle spikes in these concurrent requests?

15. Extensibility
Definition: What exactly defines the boundary between the "core text-parsing engine" and an external "language ruleset"?
Boundary: Is there a maximum number of external modules or APIs the system can support before the 360-second performance requirement is compromised?
Behavior: How does the system handle version conflicts if a new analytical module requires a different software dependency than an older one?

16. Portability
Definition: What specifically constitutes a "major cloud provider" for this project (e.g., just AWS and GCP, or also Azure and smaller Linux instances)?
Boundary: Are there any specific database technologies or proprietary cloud services being used that might secretly tie the containerized app to a specific vendor?
Behavior: What is the acceptable maximum downtime limit during a migration between these cloud providers?