# README.md

## Social Media Phone Checker

This tool checks if a given phone number is registered on popular platforms like WhatsApp, Telegram, and Facebook.

### Features
- Python-based checker for WhatsApp
- Go-based checker for Telegram
- Node.js-based checker for Facebook
- Outputs results in `output/results.json`


## Requirements
- Python 3.8+
- Node.js
- Go


## Installation

```bash
git clone E11SX/Phone.no-S.media
cd E11SX/Phone.no-S.media
bash setup.sh
```

This will:
- Create a Python virtual environment
- Install required Python dependencies
- Check for Go and Node.js
- Export a default `PHONE_NUMBER` environment variable


## Usage

Run the main script:
```bash
source venv/bin/activate
python3 main.py
```

The results will be saved in:
```
output/results.json
```


## Setting a Custom Phone Number

Before running the script, you can set a custom number:
```bash
export PHONE_NUMBER="+11234567890"
```


## Project Structure
```
.
├── checkers
│   ├── whatsapp.py
│   ├── telegram.go
│   └── facebook.js
├── main.py
├── setup.sh
├── requirements.txt
└── output/
```


## Disclaimer
!!!This tool is for educational and ethical testing purposes only. Always respect privacy and terms of service of the platforms you interact with.!!!

