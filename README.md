
# LanguageLink
**Track:** Languages
**Team:** Syed
## The problem
People who communicate with multilingual support services may send messages in languages that the service does not immediately recognise. This can delay assistance or cause messages to be sent to the wrong support team. Veritas LanguageLink aims to identify the language of a message and route it to the appropriate support queue.
## What we built
I built an AI-powered language detection and support-routing system. A user enters a sentence, and the system predicts its language, displays its confidence score and assigns it to a suitable support queue. If confidence is below 75%, the message is sent to General Support for review. The system supports English, Malay, Indonesian, Spanish and French. We also developed an experimental feature that analyses short sections of a message to identify possible mixed-language messages.
## How it works
Data: We used the Tatoeba dataset and selected 7,000 sentences for each of our five languages, giving us 35,000 sentences. We prepared the sentence text and language labels and divided the data into 28,000 training examples and 7,000 held-out test examples, using a stratified split to maintain equal language representation.
Model: I used a TF-IDF vectorizer with character n-grams of sizes 1–5 and a maximum of 50,000 features. I trained a Logistic Regression classifier because it works well with text features and can provide prediction probabilities for our routing system.
## Results
My majority-class baseline scored 20%. Our model achieved 93.13% accuracy on the held-out test data, correctly classifying 6,519 out of 7,000 sentences.
The model performed particularly well on English, Spanish and French. Its main weakness was distinguishing Malay from Indonesian. These languages share many similar words and sentence structures, causing the model to confuse them.
For example, the model sometimes predicts Malay for an Indonesian sentence. My system addresses uncertain predictions by sending low-confidence messages to General Support. My also developed experimental mixed-language detection, but this feature still needs more testing.
## What we'd do next
Improve Malay and Indonesian detection by adding more varied training examples and testing additional text features.
Evaluate the mixed-language detection feature on a larger, independent dataset and improve its reliability.
## Sources
Tatoeba dataset: https://tatoeba.org/
Scikit-learn documentation: https://scikit-learn.org/stable/
Gradio documentation: https://www.gradio.app/docs
Python documentation: https://docs.python.org/3/
AI assistance: ChatGPT (OpenAI): https://chatgpt.com/
