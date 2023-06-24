# GPT-Assistant(GUI)

_Your friendly neighborhood GTK GUI chatbot, now with bells and whistles (functions)._

## Table of Contents

- [Description](#description)
  - [Limitations](#limitations)
  - [TODO](#todo--wants--would-if-i-could)
- [Functions](#functions)
- [Usage](#usage)
- [Screenshots](#gui-screenshots)
  - [Chat UI](#chat-ui)
  - [File-Manager](#file-manager)
  - [Settings](#settings-tab)
  - [Read CSV and Plot with Python](#read-csv-and-use-python-to-plot-older-gui)


## Description

Chatbot built with TKinter GUI and a bunch of functions.

* History is in practice in memory. (save to file with /save)
* File manager - View saved files, load text files into the chat.
* Has tiktoken calculation for total tokens/cost for both the input field and the total conversation. (at the moment it assumes all messages are gpt-4 as I have no way atm to tell which agent is responding in that part of the app)

### Limitations

* Pretty basic GUI - Not threaded, so it freezes when the bot is thinking.
* Can not copy from the chat window. (Workaround, ask it to write to file)
* I don't know python.
* Probably many more.

### TODO / Wants / Would if I could

- [ ] Integration with Vector DB (A tab for it in the UI with upload/search/embed/etc)
- [x] Settings tab for configuring the parameters of the different agents (somewhat done)
- [ ] Streamed responses live updated in UI. Not sure how to get around threading (or how to do it generally), especially for running python code.
- [ ] Refactor the UI code to be more modular and less spaghetti
- [ ] Token counter / Cost counter
- [ ] Probably more

## Functions

* /help - lists these commands
* /csv - csv handler
* /python - python interpreter
* /kb - knowledge base handler [read, write, list]
* /history - history handler [read, write, list] - Useful if you only want to summarize history
* /write - file writer chooses between `data/`, `data/code/` and `data/code/projects` depending on what it's asked to write
* /read - file reader
* /edit - file editor (takes line range, text)
* /wikidata - wikidata sparql handler
* /image - image to text captioner
* /scrape - web scraper 
* /save 'filename' - saves entire conversation history to file in history folder

### Not "functions" but commands/strict prompts

* review - performs a review of the code following a strict response format
* brainstorm [n] - returns a list of n ideas for the topic following a strict response format
* ticket - creates a ticket for the brainstorm following a strict response format
* help - returns a list of all available functions

Example Usecase: /read_file code.ts/py/rs/etc -> /review -> /edit_file code.ts/py/rs/etc

## Usage

* Create a .env file in the root of the project:
  - OPENAI_API_KEY=your-api-key
  - PINECONE_API_KEY=your-api-key
  - PINECONE_ENVIRONMENT=your-environment
* `pip install -r requirements.txt` to install dependencies
* `python main.py` to run the chatbot


## GUI Screenshots

### Chat UI (With token and cost counters)
![GUI with Token Count](screenshots/guui.png)

### File-Manager
![Alt text](screenshots/filemanager.png)

### Settings Tab
![Settings tab](screenshots/setting.png)

### Read CSV and Use Python to plot (older GUI)
![Read CSV and Use Python to plot](screenshots/image-2.png)
