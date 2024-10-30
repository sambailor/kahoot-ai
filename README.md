# Kahoot AI (Kahoot Answer Bot)

FORK:
- Problem: The original repository finds the Questions and Answers on a Kahoot page via screenshots, coordinates, and an OCR to extract the text. This causes issues when a the browser or display are a different size than what the source code expects (1440p).
- I want to use the web elements directly. I have two ideas on how to do this.
  1. Create a Chrome Extension, which will find the question and answers in the DOM. Send the questions and answers as a request to a flask API, which will interact with ChatGPT. Flask will be hosted locally for now, but perhaps one day I could host it online. The user will still need their own OpenAI API keys.
  2. Use Chrome DevTools Protocol + Python or Selenium + Python to interact with an open Kahoot tab. No need for Flask API or Chrome extension here, since all work done is within python scripts.
      - https://stackoverflow.com/questions/70713643/retrieve-html-from-web-page-with-chrome-dev-tools https://github.com/marty90/PyChromeDevTools

Original script (kahoot_god.py) automatically screenshots a Kahoot game's questions and options, processes them, and then consults with OpenAI's GPT-4 to get the most likely answer. View the video here [Kahoot god video](https://www.youtube.com/watch?v=G0i_xx-6G-4&ab_channel=TheCodingSloth)

## Prerequisites

- Python 3.6 or above
- Tesseract OCR
- OpenAI API key

## Installation & Setup

1. Clone the repository
2. Install the necessary Python packages (make a venv) and then in the terminal type `pip install -r requirements.txt`
3. Make sure you have Tesseract installed. If not, you can download it from [here](https://github.com/tesseract-ocr/tessdoc). Remember the path where `tesseract.exe` is located.

4. Update the `pytesseract.pytesseract.tesseract_cmd` in the script with your path to `tesseract.exe`.
5. Update the openai.api_key in the script with your OpenAI API key. If you don't have one, you can sign up at [OpenAI](https://platform.openai.com/).
6. Update the coordinates in the scripts to fit your needs, if the current ones don't work

## Using the Program

1. Launch your Kahoot game (or whatever you wanna do) and make sure it's visible on your screen.
2. Run the script with this command: `python [script-name.py]` ex: `python kahoot_god.py`
3. Whenever you're ready to run the script press `ctrl+alt+t` (You can modify these in the script too)

## Notes
The script uses screen coordinates to determine where to screenshot for questions and answers. You may need to adjust these if you have a different screen resolution or if Kahoot's layout changes.

The bot makes educated guesses based on the information it receives. It's not guaranteed to always get the right answer, especially if questions require knowledge of images or videos.

This bot is made for use on a 1440p screen. It will not work on any other resolution

## Contributions

Contributions are welcome! Please make sure to test your changes thoroughly before submitting a pull request.
