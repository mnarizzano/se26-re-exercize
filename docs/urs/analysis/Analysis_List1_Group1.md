# RE - Requirement Engineering — Exercise (List 1)

**General "practical" rule:**
*The system shall + precise verb + precise object + precise metric + condition/threshold + output*

**Example:**
*The system shall highlight all sentences longer than 15 words in the analysis report.*

---

## 1. Readability: the system have to check sentence length and its complexity

### AMBIGUITY
- "check" → generic; check for what? evaluate / measure / flag…?
- "sentence length" → what is sentence length? number of words? characters? subordinate clauses?
- "complexity" → which kind of complexity? lexical? syntactic? semantic? structural?

### INCOMPLETENESS
- No output specified: score, warning, highlights, report?
- No language specified
- No threshold for what counts as too long or too complex
- No definition of how complexity is measured

### Conflictual
Can be partially conflicting with: *"The system shall evaluate the readability of the text and provide a readability score by analyzing sentence length, word complexity, and text structure."* Complexity can also differ from language to language.

### How to modify it?
*The system shall evaluate the readability of English texts by measuring: (1) the number of words in each sentence, and (2) the number of subordinate clauses in each sentence. The system shall assign a readability score from 0 to 100 and highlight all sentences longer than 25 words or containing more than 2 subordinate clauses.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall measure the length of each sentence as the number of words it contains.
- **R2** - The system shall measure sentence syntactic complexity as the number of subordinate clauses contained in each sentence.
- **R3** - The system shall assign a readability score from 0 to 100 based on sentence length and syntactic complexity.
- **R4** - The system shall highlight sentences longer than 25 words or containing more than 2 subordinate clauses in the analysis report.

---

## 2. Suggestion: the system have to give suggestion on correction on weak part of the text

### AMBIGUITY
- "suggestion" – what kind? vocabulary, grammar, style, restructuring?
- "correction" – corrections of what? spelling errors, grammar, logic?
- "weak part" – how is weakness defined? low readability? repetition? poor structure?
- "give" – how? inline highlight, side panel, pop-up, report section?

### INCOMPLETENESS
- No definition of what makes a part of the text "weak"
- No specification of how suggestions are displayed to the user
- No mention of languages supported
- No priority or severity level for suggestions

### Conflictual
May overlap with requirement: *"The system should highlight paragraphs that could be improved...and suggest improvements."* Both address suggestions but define scope differently.

### How to modify it?
*The system shall identify text segments scoring below a configurable quality threshold (based on readability score, sentence length, and vocabulary repetition) and display inline improvement suggestions including vocabulary alternatives, sentence restructuring, and grammar corrections.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall identify sentences with a readability score below the configurable threshold.
- **R2** - The system shall suggest vocabulary alternatives for words flagged as overused or overly complex.
- **R3** - The system shall suggest restructuring for sentences exceeding 25 words.
- **R4** - The system shall display all suggestions as inline annotations linked to the affected text segment.

---

## 3. Plot Coherence: the system has to find the key facts of the text and check if there is coherence among it

### AMBIGUITY
- "key facts" – what counts as a key fact? characters, events, dates, locations?
- "coherence" – what type? chronological, logical, character consistency?
- "check" – how? automated scoring, manual flagging, visual map?
- "among it" – grammatically ambiguous; coherence among what exactly?

### INCOMPLETENESS
- No definition of how key facts are extracted (NLP, user-defined, etc.)
- No output format specified (score, report, visual map)
- No threshold for what constitutes an incoherence
- No mention of how contradictions are reported to the user

### Conflictual
May conflict with "Character Interaction Map" and "Sentiment/Tone Analysis" requirements, as all three analyze narrative elements but with undefined boundaries.

### How to modify it?
*The system shall extract named entities (characters, locations, events) and their relationships from the manuscript, then detect logical contradictions or chronological inconsistencies and report them in a coherence report with severity ratings.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall extract named entities (characters, locations, events, dates) from the manuscript text.
- **R2** - The system shall build a relationship graph linking entities to the scenes/chapters where they appear.
- **R3** - The system shall detect contradictions (e.g., a character appearing after being removed from the story) and flag them as coherence errors.
- **R4** - The system shall generate a coherence report listing each detected issue with its location, severity (high/medium/low), and a description.

---

## 4. The system shall evaluate the readability of the text and provide a readability score by analyzing sentence length, word complexity, and text structure.

### AMBIGUITY
- "readability score" – what scale? 0-100? Flesch-Kincaid grade?
- "word complexity" – syllable count? frequency in language? domain-specific?
- "text structure" – paragraph length? heading usage? section organization?

### INCOMPLETENESS
- No specific formula or algorithm identified (Flesch, Gunning Fog, etc.)
- No language specification (English only or multilingual?)
- No output format (number, grade level, label like "easy/medium/hard")
- No mention of how the score is displayed to the user

### Conflictual
Partially overlaps with *"Readability: the system have to check sentence length and its complexity"* – both address the same concept with different levels of precision.

### How to modify it?
*The system shall compute a readability score from 0 to 100 for each uploaded text using the Flesch Reading Ease formula, based on average sentence length (words per sentence) and average syllable count per word, and display the score alongside a grade label (Easy / Moderate / Difficult).*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall calculate the average number of words per sentence in the uploaded text.
- **R2** - The system shall calculate the average number of syllables per word in the uploaded text.
- **R3** - The system shall compute a Flesch Reading Ease score from 0 to 100 using the calculated averages.
- **R4** - The system shall display the readability score with a corresponding label: Easy (>=70), Moderate (50-69), Difficult (<50).

---

## 5. The system shall detect sentence length problems by measuring the number of words in each sentence and identifying extremes.

### AMBIGUITY
- "problems" – what constitutes a problem? too long? too short? both?
- "extremes" – no threshold defined; extreme compared to what baseline?
- "measuring" – automatic or requiring user action?

### INCOMPLETENESS
- No thresholds for what counts as too long or too short
- No indication of how results are presented (highlight, report, count)
- No mention of whether the user can configure thresholds

### Conflictual
Overlaps with the readability requirement since both measure sentence length, risking duplicate analysis.

### How to modify it?
*The system shall flag any sentence with fewer than 5 words or more than 40 words, highlighting it in the text and categorizing it as "too short" or "too long" in the analysis report.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall count the number of words in each sentence of the uploaded text.
- **R2** - The system shall flag sentences with fewer than 5 words as "too short."
- **R3** - The system shall flag sentences with more than 40 words as "too long."
- **R4** - The system shall highlight flagged sentences in the text view and list them in the analysis report with their word count.

---

## 6. The system shall allow users to export the report by providing options in formats such as PDF, TXT, and DOCX.

### AMBIGUITY
- "such as" – implies the list is not exhaustive; which formats are mandatory?
- "report" – which report? the full analysis? a summary? all reports?

### INCOMPLETENESS
- No mention of whether formatting/styling is preserved across export types
- No specification of where the exported file is saved or downloaded
- No mention of whether charts/visuals are included in exports

### Conflictual
No direct conflicts with other requirements.

### How to modify it?
*The system shall allow users to export the complete analysis report in PDF, TXT, and DOCX formats via a download button, preserving all text content, tables, and charts in PDF and DOCX exports.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall provide an export button on the report view page.
- **R2** - The system shall support exporting the report in PDF, TXT, and DOCX formats.
- **R3** - The system shall preserve text content, tables, and visual charts in PDF and DOCX exports.
- **R4** - The system shall trigger a browser download of the exported file upon user request.

---

## 7. Character Interaction Map: A visual matrix showing which characters appear together and their distribution throughout the timeline.

### AMBIGUITY
- "visual matrix" – what kind? heatmap, graph, table, network diagram?
- "appear together" – same chapter? same scene? same paragraph? same sentence?
- "timeline" – what defines the timeline? chapters, pages, word count?
- "distribution" – frequency of co-occurrence? total scene count?

### INCOMPLETENESS
- No definition of how characters are identified (user-defined list or auto-detected)
- No specification of interactivity (clickable? filterable? zoomable?)
- No export or save option mentioned for the map

### Conflictual
Partially overlaps with Plot Coherence requirement, as both analyze character presence across the narrative.

### How to modify it?
*The system shall automatically detect character names (proper nouns appearing 3+ times) and generate an interactive co-occurrence matrix showing how often each pair of characters appears in the same chapter, displayed as a heatmap with chapter-based timeline filtering.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall detect character names as proper nouns appearing 3 or more times in the manuscript.
- **R2** - The system shall calculate the co-occurrence count for each pair of characters per chapter.
- **R3** - The system shall display the co-occurrence data as a heatmap matrix with characters on both axes.
- **R4** - The system shall allow users to filter the heatmap by chapter range using a timeline slider.

---

## 8. Sentiment/Tone Analysis: Tracking the emotional arc of scenes to ensure the "mood" aligns with the narrative intent.

### AMBIGUITY
- "emotional arc" – what emotions are tracked? joy, sadness, tension, fear?
- "scenes" – how is a scene defined? by chapter? by paragraph break? by user markers?
- "narrative intent" – who defines intent? the author? the system?
- "aligns" – how is alignment measured?

### INCOMPLETENESS
- No emotion categories or sentiment scale defined
- No specification of how "narrative intent" is captured (user input? genre rules?)
- No output format (chart, report, per-scene labels)
- No mention of which NLP model or technique is used

### Conflictual
May conflict with Plot Coherence since both analyze narrative flow but from different perspectives (emotion vs. facts).

### How to modify it?
*The system shall perform sentiment analysis on each chapter, classifying the dominant tone as positive, negative, or neutral with a confidence score from 0 to 1, and display the results as a line chart showing the emotional arc across the full manuscript.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall divide the manuscript into chapters (based on heading markers or user-defined breaks).
- **R2** - The system shall classify the dominant sentiment of each chapter as positive, negative, or neutral with a confidence score (0 to 1).
- **R3** - The system shall display a line chart plotting sentiment scores across chapters to visualize the emotional arc.
- **R4** - The system shall allow users to click on any data point in the chart to view the corresponding chapter text and sentiment details.

---

## 9. Count the occurrence of each word to detect and signal repetitions and overused vocabulary.

### AMBIGUITY
- "each word" – does this include stop words (the, a, is)? case-sensitive?
- "signal" – how? popup, color coding, report section?
- "overused" – compared to what baseline? absolute count? percentage?
- "repetitions" – exact matches only, or also synonyms/lemmas?

### INCOMPLETENESS
- No threshold for when a word is considered overused
- No exclusion list for common/stop words
- No specification of the output or visualization
- Missing: should the system suggest synonyms?

### Conflictual
Overlaps with the Suggestion requirement, which also may flag vocabulary issues.

### How to modify it?
*The system shall count occurrences of each word (excluding a predefined stop-word list), normalize by lemma and case, flag words appearing more than 0.5% of total word count as overused, and display results in a frequency table sorted by count with synonym suggestions.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall tokenize the text and count each word occurrence, case-insensitive and lemmatized.
- **R2** - The system shall exclude common stop words (defined in a configurable stop-word list) from the count.
- **R3** - The system shall flag words exceeding 0.5% of total word count as "overused."
- **R4** - The system shall display a frequency table of flagged words with count, percentage, and synonym suggestions.

---

## 10. The system should highlight paragraphs that could be improved, based on the previous analysis, and suggest improvements like vocabulary alternatives, dividing long phrases into shorter ones, formatting.

### AMBIGUITY
- "previous analysis" – which analysis? all of them combined? a specific one?
- "could be improved" – by what criteria? score threshold?
- "formatting" – what kind? paragraph spacing? heading hierarchy? bullet lists?
- "highlight" – how? color, underline, sidebar marker?

### INCOMPLETENESS
- No threshold for triggering improvement suggestions
- No prioritization of suggestions (which to show first)
- No mention of whether the user can accept/reject suggestions
- No specification of how suggestions are generated (rule-based, AI-based)

### Conflictual
Directly overlaps with the "Suggestion" requirement – both promise text improvement suggestions with unclear scope boundaries.

### How to modify it?
*The system shall highlight paragraphs scoring below the 30th percentile across readability, repetition, and sentence-length analyses, and display a prioritized list of improvement suggestions (vocabulary alternatives, sentence splitting, formatting changes) in a side panel, allowing users to accept or dismiss each suggestion.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall compute a composite quality score for each paragraph based on readability, repetition, and sentence length metrics.
- **R2** - The system shall highlight paragraphs scoring below the 30th percentile with a yellow background.
- **R3** - The system shall generate improvement suggestions for each highlighted paragraph, including vocabulary alternatives and sentence splitting options.
- **R4** - The system shall display suggestions in a side panel and allow users to accept or dismiss each suggestion individually.

---

## 11. Security: the user session have to be isolated of others session

### AMBIGUITY
- "isolated" – data isolation? process isolation? network isolation?
- "session" – browser session? server-side session? authentication context?
- "others session" – other users, or other sessions of the same user?

### INCOMPLETENESS
- No specification of isolation mechanism (tokens, sandboxing, separate DB schemas)
- No mention of session timeout or expiration policy
- No mention of authentication method (login, OAuth, SSO)
- No mention of authorization or role-based access

### Conflictual
Related to *"The system shall ensure database security by storing data in an encrypted format"* – both address security but at different layers (session vs. storage).

### How to modify it?
*The system shall enforce session isolation by assigning each authenticated user a unique session token, ensuring that no user can access, modify, or view the data or analysis results of another user's session.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall assign a unique, cryptographically random session token to each authenticated user upon login.
- **R2** - The system shall validate the session token on every API request and reject requests with invalid or expired tokens.
- **R3** - The system shall ensure that each user's uploaded texts and analysis results are accessible only through their own authenticated session.
- **R4** - The system shall expire user sessions after 30 minutes of inactivity.

---

## 12. Language support: the system support text in many languages

### AMBIGUITY
- "many languages" – how many? which ones? top 10 by speakers? EU languages?
- "support" – support for what? input, analysis, UI, export?
- "text" – all features work in all languages, or only basic ones?

### INCOMPLETENESS
- No list of supported languages
- No specification of which features work per language
- No mention of character encoding requirements (UTF-8, etc.)
- No fallback behavior for unsupported languages

### Conflictual
May conflict with readability and NLP features that may only work accurately in English, creating a gap between claimed support and actual capability.

### How to modify it?
*The system shall support text analysis in English, Italian, Spanish, French, and German. For each supported language, the system shall provide readability scoring, sentence length detection, and word frequency counting. Unsupported languages shall trigger a clear error message.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall accept text input in English, Italian, Spanish, French, and German (UTF-8 encoding).
- **R2** - The system shall apply language-specific readability formulas for each supported language.
- **R3** - The system shall use language-specific stop-word lists and lemmatization for word frequency counting.
- **R4** - The system shall display an error message "Language not supported" when the detected language is not in the supported list.

---

## 13. The system shall provide a simple and user friendly interface by allowing users to complete main actions (upload, analyze, export) in no more than 3 steps.

### AMBIGUITY
- "simple and user friendly" – subjective; cannot be tested objectively
- "3 steps" – what counts as a step? a click? a page navigation? a form submission?
- "main actions" – are upload, analyze, and export the only main actions?

### INCOMPLETENESS
- No accessibility requirements (WCAG level)
- No specification of supported browsers or devices
- No mention of responsive design for mobile
- No error-handling UX requirements

### Conflictual
No direct conflicts, but the 3-step constraint may conflict with complex features like Character Interaction Map configuration.

### How to modify it?
*The system shall allow users to complete the upload-analyze-export workflow in no more than 3 user interactions (clicks or form submissions). The interface shall conform to WCAG 2.1 AA accessibility standards and support Chrome, Firefox, Safari, and Edge.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall allow users to upload a document in one click (file picker or drag-and-drop).
- **R2** - The system shall start analysis with one click after upload, with no additional configuration required.
- **R3** - The system shall allow report export in one click from the results page.
- **R4** - The system shall conform to WCAG 2.1 Level AA accessibility standards.

---

## 14. The system shall ensure database security by storing data in an encrypted format and restricting access to authorized users only.

### AMBIGUITY
- "encrypted format" – what encryption? AES-256? at rest? in transit? both?
- "authorized users" – authorized how? by role? by account ownership?
- "restricting access" – at the database level? application level? API level?

### INCOMPLETENESS
- No specification of encryption algorithm or key management
- No mention of data backup encryption
- No audit logging requirements
- No data retention or deletion policy

### Conflictual
Complements but may overlap with session isolation requirement – need clear boundary between session-level and storage-level security.

### How to modify it?
*The system shall encrypt all stored user data at rest using AES-256 encryption, manage encryption keys through a dedicated key management service, and enforce role-based access control (RBAC) so that each user can only access their own data.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall encrypt all user data at rest using AES-256 encryption.
- **R2** - The system shall manage encryption keys using a dedicated key management service (e.g., AWS KMS or equivalent).
- **R3** - The system shall enforce role-based access control, restricting each user to their own data.
- **R4** - The system shall log all data access events for audit purposes, including user ID, timestamp, and action performed.

---

## 15. Performance: The system must analyze a standard 100,000-word .docx or .txt manuscript and generate the final diagnostic report in under 360 seconds.

### AMBIGUITY
- "standard" – what makes a manuscript standard? plain text? with images? with tables?
- "final diagnostic report" – which analyses does this include? all of them?
- "analyze" – does this include all analysis types or a specific subset?

### INCOMPLETENESS
- No specification of hardware/infrastructure baseline for the 360s target
- No mention of concurrent user load during performance measurement
- No degradation behavior defined (what happens if it exceeds 360s?)
- No mention of progress feedback to the user during analysis

### Conflictual
May conflict with the scope of analyses – adding more features (sentiment, character map) increases processing time and may make 360s infeasible.

### How to modify it?
*The system must complete all enabled analyses (readability, sentence length, word frequency, coherence, sentiment) on a 100,000-word plain-text .docx or .txt file and render the diagnostic report in under 360 seconds, measured on a single instance with 4 vCPUs and 8 GB RAM under single-user load.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall complete all enabled analyses on a 100,000-word document in under 360 seconds.
- **R2** - The performance target shall be measured on a single containerized instance with 4 vCPUs and 8 GB RAM.
- **R3** - The system shall display a progress indicator during analysis showing estimated time remaining.
- **R4** - If analysis exceeds 360 seconds, the system shall log a performance warning and still deliver partial results.

---

## 16. Portability: The application must be fully containerized (e.g., using Docker) to allow seamless deployment and migration across major cloud providers (such as AWS or Google Cloud) without modifying the application source code.

### AMBIGUITY
- "fully containerized" – single container or multi-container (Docker Compose, K8s)?
- "seamless" – subjective; zero downtime? no manual steps?
- "major cloud providers" – which ones specifically? AWS, GCP, Azure?
- "without modifying the application source code" – configuration changes allowed?

### INCOMPLETENESS
- No specification of container runtime (Docker, Podman, containerd)
- No mention of environment configuration (env vars, config files)
- No CI/CD pipeline requirements
- No mention of data persistence across migrations

### Conflictual
No direct conflicts, but the performance requirement (360s) must be validated across different cloud environments.

### How to modify it?
*The application shall be packaged as a Docker container image compatible with Docker Engine 20+, deployable on AWS ECS, Google Cloud Run, and Azure Container Instances using only environment variables for configuration, with no source code changes required between providers.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The application shall be packaged as a single Docker container image using a Dockerfile in the project repository.
- **R2** - The container image shall run on Docker Engine 20+ and be compatible with AWS ECS, Google Cloud Run, and Azure Container Instances.
- **R3** - All environment-specific settings (database URL, API keys, ports) shall be configurable via environment variables.
- **R4** - The project shall include a docker-compose.yml for local development and testing.

---

## 17. The system should allow users to share their work with other registered users.

### AMBIGUITY
- "share" – share what? the text? the analysis report? both? read-only or editable?
- "work" – uploaded manuscripts? generated reports? settings/configurations?
- "other registered users" – by email? by username? anyone on the platform?

### INCOMPLETENESS
- No permission model defined (view only, edit, comment)
- No mention of sharing mechanism (link, invite, search users)
- No mention of revoking shared access
- No notification system for when content is shared with a user

### Conflictual
May conflict with session isolation requirement (*"user session have to be isolated"*) – sharing inherently requires cross-session data access.

### How to modify it?
*The system shall allow users to share their analysis reports with other registered users by entering the recipient's email address, granting read-only access. The sharing user shall be able to revoke access at any time.*

### SPLIT – Atomicity
Too many concepts → break into atomic requirements:

- **R1** - The system shall provide a "Share" button on the report view, allowing the user to enter a registered user's email address.
- **R2** - The system shall grant the recipient read-only access to the shared report.
- **R3** - The system shall allow the original user to revoke shared access at any time from a "Shared With" management panel.
- **R4** - The system shall send an email notification to the recipient when a report is shared with them.
