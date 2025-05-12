# VAF BG Article Quiz

This project is a web-based application that allows users to generate quizzes from article content using Google's Gemini AI. Users can input an article (HTML format), provide custom instructions, select a Gemini model, and set the generation temperature. The application then calls the Gemini API to produce a quiz in JSON format, which is subsequently rendered as an interactive, step-by-step quiz.

## Features

*   **Gemini API Integration:** Utilizes the Google Gemini API for quiz generation.
*   **API Key Management:** Securely stores the user's Gemini API Key in browser local storage.
*   **Customizable Generation:**
    *   User-defined instructions for the AI.
    *   Adjustable temperature for controlling AI creativity.
    *   Selection from available Gemini models.
*   **Input Article:** Accepts article content in HTML format.
*   **JSON Output:** Displays the raw JSON output from the AI.
*   **Interactive Quiz UI:**
    *   Presents questions one by one.
    *   Allows users to select an answer.
    *   Provides immediate feedback (correct/incorrect) and explanations.
    *   Shows difficulty level for each question.
    *   Calculates and displays the final score.
    *   Option to restart the quiz.
*   **Responsive Design:** Styled with Tailwind CSS for a modern and responsive user interface.

## How to Use

1.  **Open `index.html`:** Launch the `index.html` file in a web browser.
2.  **Set API Key:**
    *   Enter your Google Gemini API Key in the "Setup Gemini API Key" section.
    *   Click "Save & Initialize API". A success message will confirm initialization.
3.  **Create Quiz:**
    *   Once the API key is saved, the "Create Quiz from Article" button will be enabled. Click it to open the generation dialog.
    *   **Instructions:** Review or modify the prefilled quiz generation instructions.
    *   **Temperature:** Adjust the temperature slider (0 to 2) as needed.
    *   **Model:** Select the desired Gemini model from the dropdown.
    *   **Article Content:** Paste or modify the HTML content of the article you want to generate a quiz from.
    *   Click "Generate Quiz".
4.  **View Output:**
    *   A progress indicator will show while the quiz is being generated.
    *   The raw JSON output from the AI will be displayed by default.
    *   If the JSON is valid, an "Show Interactive Quiz" button will appear. Click it to switch to the interactive quiz interface.
5.  **Take the Quiz:**
    *   Answer each question and click "Ստուգել պատասխանը" (Check Answer).
    *   Feedback and explanation (if provided by the AI) will be shown.
    *   Click "Հաջորդ հարցը" (Next Question) to proceed.
    *   After the last question, click "Տեսնել արդյունքները" (See Results) to view your final score.
    *   You can restart the quiz using the "Կրկին փորձել" (Try Again) button.
6.  **Toggle Views:** Use the "Show Raw JSON" and "Show Interactive Quiz" buttons to switch between the raw AI output and the quiz UI.

## Technologies Used

*   HTML5
*   CSS3 (Tailwind CSS, custom styles)
*   JavaScript (ES Modules)
*   Google Gemini API (`@google/genai` SDK via esm.sh)

## Quiz JSON Schema

The application expects the AI to generate a JSON object adhering to a specific schema, which includes:
*   `quizTitle` (string)
*   `quizDescription` (string)
*   `questions` (array of objects), where each question object has:
    *   `question` (string)
    *   `options` (array of strings)
    *   `answer` (number, 0-indexed)
    *   `articleIds` (array of strings, e.g., for referencing parts of the source article)
    *   `explanation` (string)
    *   `difficulty` (string, e.g., "Easy", "Medium", "Hard")

The schema is provided to the AI as part of the prompt.