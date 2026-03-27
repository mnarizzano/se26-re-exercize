Requirements:


## Lista 1



* Readability  : the system have to check sentence length and its complexity
* Suggestion  : the system have to give suggestion on correction on weak part of the text
* Plot Coherence  : the system has to find the key facts of the text and check if there is coherence among it
* The system shall evaluate the readability of the text and provide a readability score by analyzing sentence length, word complexity, and text structure.
* The system shall detect sentence length problems by measuring the number of words in each sentence and identifying extremes.
* The system shall allow users to export the report by providing options in formats such as PDF, TXT, and DOCX.
* Character Interaction Map: A visual matrix showing which characters appear together and their distribution throughout the timeline.
* Sentiment/Tone Analysis: Tracking the emotional arc of scenes to ensure the "mood" aligns with the narrative intent.
* Count the occurrence of each word to detect and signal repetitions and overused vocabulary.
* The system should highlight paragraphs that could be improved, based on the previous analysis, and suggest improvements like vocabulary alternatives, dividing long phrases into shorter ones, formatting.



* Security: the user session have to be isolated of others session
* Language support: the system support text in many languages
* The system shall provide a simple and user friendly interface by allowing users to complete main actions (upload, analyze, export) in no more than 3 steps.
* The system shall ensure database security by storing data in an encrypted format and restricting access to authorized users only.
* Performance: The system must analyze a standard 100,000-word .docx or .txt manuscript and generate the final diagnostic report in under 360 seconds.
* Portability: The application must be fully containerized (e.g., using Docker) to allow seamless deployment and migration across major cloud providers (such as AWS or Google Cloud) without modifying the application source code.
* The system should allow users to share their work with other registered users.
