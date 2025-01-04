
# TalentScout Hiring Assistant (Google Colab Version)

## 1. Project Overview

**TalentScout** is an AI-powered Hiring Assistant intended to streamline the initial screening of technology candidates. It:
- Collects essential candidate information (e.g., name, contact details, years of experience).
- Asks the candidate about their tech stack (e.g., Python, Django, React).
- Dynamically generates relevant technical questions to evaluate proficiency.

By leveraging **Google Generative AI (Gemini)** and **Gradio**, you can interact with this Hiring Assistant in a **Google Colab** notebook environment—no local installation required beyond a browser and a Google account.

---

## 2. Getting Started on Google Colab

### 2.1. Prerequisites
1. A **Google account** to access Google Colab.
2. A **Gemini (Google Generative AI) API key**. You can get one through Google Cloud’s [Generative AI App Builder or PaLM API console](https://ai.google.dev/aistudio).  
3. (Optional) Some familiarity with **Python** and **Gradio** is helpful but not required.

### 2.2. Importing / Opening the Colab Notebook
1. **Create a new Google Colab notebook** (or open an existing one).
2. **Copy/Paste** the TalentScout code into a Colab cell.  
3. **Replace** `"YOUR_API_KEY_HERE"` with your actual **Gemini API key** in the environment variable line.

### 2.3. Install Dependencies
Within the Colab notebook, make sure to install the required libraries. For example:
```python
!pip install google-generativeai gradio textblob langdetect
```
*(If you’re not using sentiment analysis or multilingual features, you can omit `textblob` and `langdetect`.)*

### 2.4. Run the Code
1. **Run all cells** in the notebook. 
2. When you reach the cell containing the TalentScout code (with the Gradio interface), running it will produce a **public or local URL**. 
3. **Click** or **Ctrl/Cmd+Click** the URL to open the Gradio app in a new tab.

---

## 3. Usage Guide in Colab

1. **Fill In Candidate Information**  
   - In the “Candidate Information” section, input your full name, email, phone number, years of experience, desired positions, current location, and tech stack.  
   - Click **Submit Information** to store these details.

2. **Generate Technical Questions**  
   - After submitting your info, click the **Generate Questions** button.  
   - The Hiring Assistant will automatically produce 3–5 technical questions per technology mentioned in your tech stack.

3. **Chat and Follow-Ups**  
   - Type in the **Chatbot** textbox to ask additional questions, clarify details, or provide more info.  
   - The assistant can remain context-aware thanks to the conversation history in Colab.

4. **Ending the Conversation**  
   - Type **“exit”**, **“quit”**, **“done”**, **“stop”**, or **“thank you”** to end the conversation gracefully.  
   - Once the session ends, you can still view past messages in the Colab output cells.

5. **Re-run if Needed**  
   - If you want to restart, simply **re-run** the Colab cell. This resets the conversation context unless you store it separately.

---

## 4. Technical Details

1. **Google Generative AI (Gemini)**:  
   - The language model used for question generation and conversation flow.  
   - Configured via `google-generativeai` in Colab.

2. **Gradio**:  
   - Provides the lightweight web UI directly from Colab.  
   - After running the code cell, it exposes a link to interact with the chatbot.

3. **Conversation State**:  
   - Managed via a Gradio `State` object (usually a list of `(role, message)` tuples).  
   - Ensures the assistant remembers context across multiple user inputs.

4. **Optional Enhancements**:
   - **Sentiment Analysis** (using `TextBlob`): Interprets the user’s tone or mood.  
   - **Multilingual** (using `langdetect`): Potentially detects user language for non-English conversations.  
   - **Personalization**: Adjust responses or question difficulty based on user preference or sentiment.

---

## 5. Prompt Design

1. **System Prompt**  
   - Defines the assistant’s role as a “TalentScout Hiring Assistant” and instructs it to collect specific info and generate tailored questions.  
   - In Colab, you can modify this prompt directly in the code under `system_instruction`.

2. **Info Gathering Prompt**  
   - Separate logic to gather user details—name, email, phone, years of experience, etc.

3. **Tech Stack Prompt**  
   - Asks the user for their tech stack (Python, Django, React, etc.).

4. **Technical Question Prompt**  
   - Dynamically constructed to generate 3–5 questions per listed technology.

5. **Exit Prompt**  
   - Listens for keywords (“exit,” “quit,” “done,” “stop,” “thank you”) to wrap up.

---

## 6. Challenges & Solutions

1. **Colab Session Timeouts**  
   - **Challenge**: Google Colab sessions can time out if idle too long.  
   - **Solution**: Keep the session active, or periodically re-run cells to maintain the environment.

2. **Language Detection on Short Responses**  
   - **Challenge**: A single-word response like “Yes” can falsely trigger a language switch.  
   - **Solution**: Use a safe function to detect language only for messages above a certain length.

3. **Repeated Info or Summaries**  
   - **Challenge**: The assistant may re-ask or re-summarize user details.  
   - **Solution**: Introduce a `collected_info` flag to confirm data is gathered once and avoid repetition.

4. **Potential Rate Limits**  
   - **Challenge**: Large or frequent queries may hit GPT/Gemini API rate limits in Colab.  
   - **Solution**: Optimize prompt usage, or upgrade to a plan with higher rate limits.

5. **Security & Privacy**  
   - **Challenge**: Handling personal information in a public or shared Colab environment.  
   - **Solution**: Avoid storing sensitive data in the notebook if it’s publicly shared; consider obfuscation or local storage.  

---

## Conclusion

By running TalentScout in **Google Colab**, you get a **no-hassle** environment to:
1. Quickly **prototype** the Hiring Assistant.
2. Collect candidate info and generate **relevant** technical questions.
3. **Experiment** with additional features—sentiment analysis, multilingual, personalization—without needing local setup.

**Next Steps**:
- **Fork/Copy** the Colab notebook for your own custom modifications.  
- **Store** user responses in a secure backend if you plan to scale.  
- **Integrate** with other services (e.g., email notifications, external databases) once you finalize your approach.

If you have any questions or feedback, feel free to reach out via **GitHub Issues** or your preferred support channel!

---  

**Author / Maintainer**  
- Spandan Mukherjee 

*Looking Forward :) for this opportunity*
