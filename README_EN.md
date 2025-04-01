# Cliffford Discord Bot

[繁體中文](README.md) | [English](README_EN.md)

## Introduction
Cliffford Discord Bot is a Discord bot developed using Python 3.11, leveraging the Google Gemini API to provide AI response capabilities, including text chat and image analysis. The bot supports slash commands (`/reset`, `/set`, `/unset`) to manage its behavior and uses the `console_rules.json` file for real-time rule checking to ensure responses comply with guidelines.

Bot features include:
- Interacting with users via text and images (using the Gemini API).
- Setting specific response channels (`/set` and `/unset`).
- Resetting the bot's chat state (`/reset`).
- Real-time rule checking to avoid violating rules defined in `console_rules.json`.
- Logging all console output to the `bot.log` file.

## Requirements
- Python 3.11 or 3.12 (3.11 recommended)
- Discord Bot Token x1
- Google Gemini API Key x1  
The Discord Bot Token and Gemini API Key are the most basic and essential requirements.

## Installation

### 1. Download the Project

### 2. Navigate to the Project Folder
```bash
cd Cliffford
```

### 3. Install Dependencies
Install the required packages:
```bash
pip install -r requirements.txt
```

### 4. Configure Settings
- Configure the `setting.py` file with the following content:
  ```python
  BOT_TOKEN = "your_Discord_Bot_Token"
  GEMINI_API_KEY = "your_Gemini_API_Key"
  BOT_NAME = "Cliffford"  # AI's self-identification
  BOT_VERSION = "Beta.v0.a1"  # Version (optional to modify)
  developer = "your_name"  # Bot owner's name
  developer_id = "your_Discord_ID"  # Developer/owner Discord ID
  DEFAULT_CHANNEL = "channel_ID"  # Optional; if left blank, the bot responds in any channel unless /set is used
  ```

- Configure the `main.py` file with the following content:
  ```
  genai.configure(api_key=GEMINI_API_KEY)
  text_model = genai.GenerativeModel('your_chosen_Gemini_model_name')
  vision_model = genai.GenerativeModel('your_chosen_Gemini_model_name')
  ```

### 5. Edit Rule Files
- Edit `bot_rules.json` (basic rules for AI interaction with users):
  ```json
  [
    {
      "role": "user",
      "parts": "[Rule] Please respond to all messages in Chinese"
    },
    {
      "role": "model",
      "parts": "[Response Rule] I will respond to all messages in Chinese"
    }
  ]
  ```
- Edit `console_rules.json` (for real-time rules):
  ```json
  [
    {
      "rule": "Avoid using rude or offensive language",
      "action": "Please use friendly language, or I cannot respond"
    }
  ]
  ```

## Usage

### 1. Start the Bot
Run the following in the project folder:
```bash
python main.py
```

## Interacting with the Bot on Discord
- **Text Chat**: Send a text message directly in Discord, and the bot will respond in reply form.
- **Image Analysis**: Upload an image with (optional) text description, and the bot will analyze and respond.
- **Slash Commands**:
  - `/reset`: Reset the bot's memory.
  - `/set #channel`: Set the bot to respond only in the specified channel.
  - `/unset`: Remove the channel restriction, allowing the bot to respond in all channels.

### 3. Console Interaction
- After starting, the console will prompt "Enter a question in the console (type 'exit' to quit)". You can input questions for the bot to respond to.

### 4. Logging
- All console output is simultaneously logged to the `bot.log` file in the following format:
  ```
  Date Time - INFO - User input: your_question
  Date Time - INFO - Checking against real-time rules
  Date Time - INFO - Bot response: bot_response
  ```

## Configuration Details

### `setting.py`
- `BOT_TOKEN`: Obtain this from the Discord Developer Portal.
- `GEMINI_API_KEY`: Obtain this from the Google Cloud Console.
- `bot_name`: The bot's name (how the AI identifies itself).
- `bot_version`: The bot's version number (optional to change).
- `developer`: The bot owner's name.
- `DEFAULT_CHANNEL`: Optional default response channel ID (leave blank for no default).

### `console_rules.json`
- Defines real-time rules in the following format:
  ```json
  [
    {
      "rule": "rule_description",
      "action": "response_when_violated"
    }
  ]
  ```
- Rules are checked in real-time with each message processed.

## FAQ

### 1. Slash Commands Not Working
- Ensure `BOT_TOKEN` is correctly set and the bot has "Use Application Commands" permission.
- Restart the program and check the console logs.

### 2. Gemini API Errors
- Verify that `GEMINI_API_KEY` is valid and check if the model name (e.g., `gemini-2.0-flash`) is correctly specified.
- Ensure the API Key has permission to use the specified Gemini model and has remaining quota.

## Contribution
If you have suggestions for new features or find bugs, please contact me.

## License
Please read the `LICENSE` file.