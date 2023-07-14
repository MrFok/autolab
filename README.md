# AutoLab API

![Version](https://img.shields.io/badge/version-0.1.1_alpha-blue)

AutoLab is a proprietary API developed by Altum Labs. It's designed to convert wet lab procedures into a procedural guide in an effortless and accurate way. It accepts a .mp4 file of a wet lab procedure and transforms it into a step-by-step guide.

**Please note that this software is not open source and cannot be used without the express permission of Altum Labs.**

## Features

- Transcription of audio from a wet lab .mp4 file using Google Speech.
- Generation of a step-by-step procedural guide from the transcription using GPT-4.

## Installation

This project runs on Python 3.10.

This software is proprietary and its use is restricted. For installation details, please contact Altum Labs. To set up the system, cd into the autolab directory and install the packages with pip or conda. This will install the autolab package in editable mode as well as any dependencies.

```bash
pip install -e .
```

or with conda:

```bash
conda develop .
```

### Environment Variables

The following environment variables must be specified in either a dotenv or in the operating system.

OPENAI_API_KEY
SUPABASE_URL
SUPABASE_SERVICE_KEY
SUPABASE_BUCKET_NAME
PROJECT_ID
RECOGNIZER_ID
GOOGLE_APPLICATION_CREDENTIALS
TMP_DIR

## Important Directories

stt_transcriptions - Contains the scripts used to transcribe mp4 or mp3 files using the Google Cloud Speech To Text (STT) v2 API.  
instruction_generator - Contains the scripts used to convert STT transcriptions into a clean lab procedure using GPT-4.

## Running the tests

TODO:
You can create your own tests by running the following Python script. You will need to specify a video destination in config.json.
Note that files must be deleted from the tmp/ directory before generate_procedure is called.

```python
from autolab import AutoLab

# Initialize autolab
lab = AutoLab()

# Transcribe a video and generate a procedure
# Use schema in data/autolab_schema.json
procedure = lab.generate_procedure('config.json')

# Returns a json containing the procedure
print(procedure)

```

## Build and Deploy

Run ./build.sh in the project directory to run the build the project for AWS Lambda deployment. This will generate a autolab.zip file in the ./build/ directory.

If you are getting a permissions error, assure that build.sh has execution permissions.

```bash
chmod +x build.sh
```

## Built with

- FFMPEG - used to convert mp4 files to mp3 files and segment them into 60-second clips
- Google Cloud Speech to Text v2 API - used to transcribe mp3 files
- GPT-4 - used to generate a clean lab procedure from the transcription

## Authors

- **Ricky Fok** - _Initial work_ - [FoksWok](https://github.com/FoksWok)
- **Izzy Qian** - _Initial work_ - [izzyaltum](https://github.com/izzyaltum)
- **Grant Rinehimer** - _Initial work_ - [AtomicAudit](https://github.com/AtomicAudit)
