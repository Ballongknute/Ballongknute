<h1 align="center">AIá Ballongknute</h1>

<p align="center">
  <strong>A framework to enable multimodal models to operate a computer.</strong>
</p>
<p align="center">
  Using the same inputs and outputs as a human operator, the model views the screen and decides on a series of mouse and keyboard actions to reach an objective. 
</p>


<!--
:rotating_light: **OUTAGE NOTIFICATION: gpt-4-vision-preview**
**This model is currently experiencing an outage so the self-operating computer may not work as expected.**
-->


## Key Features
- **Compatibility**: Designed for various multimodal models.
- **Integration**: Currently integrated with **GPT-4v, Gemini Pro Vision, and LLaVa.**
- **Future Plans**: Support for additional models.

## Run `Self-Operating Computer`

1. **Install the project**
```
pip install self-operating-computer
```
2. **Run the project**
```
operate
```
3. **Enter your OpenAI Key**: If you don't have one, you can obtain an OpenAI key [here](https://platform.openai.com/account/api-keys)


### Alternatively installation with `.sh`

1. **Clone the repo** to a directory on your computer:
```
git clone https://github.com/OthersideAI/self-operating-computer.git
```
2. **Cd into directory**:

```
cd self-operating-computer
```

3. **Run the installation script**: 

```
./run.sh
```



## Using `operate` Modes

### Multimodal Models  `-m`
An additional model is now compatible with the Self Operating Computer Framework. Try Google's `gemini-pro-vision` by following the instructions below. 

Start `operate` with the Gemini model
```
operate -m gemini-pro-vision
```

**Enter your Google AI Studio API key when terminal prompts you for it** If you don't have one, you can obtain a key [here](https://makersuite.google.com/app/apikey) after setting up your Google AI Studio account. You may also need [authorize credentials for a desktop application](https://ai.google.dev/palm_docs/oauth_quickstart). It took me a bit of time to get it working, if anyone knows a simpler way, please make a PR.

### Locally Hosted LLaVA Through Ollama
If you wish to experiment with the Self-Operating Computer Framework using LLaVA on your own machine, you can with Ollama!   
*Note: Ollama currently only supports MacOS and Linux*   

First, install Ollama on your machine from https://ollama.ai/download.   

Once Ollama is installed, pull the LLaVA model:
```
ollama pull llava
```
This will download the model on your machine which takes approximately 5 GB of storage.   

When Ollama has finished pulling LLaVA, start the server:
```
ollama serve
```

That's it! Now start `operate` and select the LLaVA model:
```
operate -m llava
```   
**Important:** Error rates when using LLaVA are very high. This is simply intended to be a base to build off of as local multimodal models improve over time.

Learn more about Ollama at its [GitHub Repository](https://www.github.com/ollama/ollama)

### Voice Mode `--voice`
The framework supports voice inputs for the objective. Try voice by following the instructions below. 
**Clone the repo** to a directory on your computer:
```
git clone https://github.com/OthersideAI/self-operating-computer.git
```
**Cd into directory**:
```
cd self-operating-computer
```
Install the additional `requirements-audio.txt`
```
pip install -r requirements-audio.txt
```
**Install device requirements**
For mac users:
```
brew install portaudio
```
For Linux users:
```
sudo apt install portaudio19-dev python3-pyaudio
```
Run with voice mode
```
operate --voice
```

### Optical Character Recognition Mode `-m gpt-4-with-ocr`
The Self-Operating Computer Framework now integrates Optical Character Recognition (OCR) capabilities with the `gpt-4-with-ocr` mode. This mode gives GPT-4 a hash map of clickable elements by coordinates. GPT-4 can decide to `click` elements by text and then the code references the hash map to get the coordinates for that element GPT-4 wanted to click. 

Based on recent tests, OCR performs better than `som` and vanilla GPT-4 so we made it the default for the project. To use the OCR mode you can simply write: 

 `operate` or `operate -m gpt-4-with-ocr` will also work. 

### Set-of-Mark Prompting `-m gpt-4-with-som`
The Self-Operating Computer Framework now supports Set-of-Mark (SoM) Prompting with the `gpt-4-with-som` command. This new visual prompting method enhances the visual grounding capabilities of large multimodal models.

Learn more about SoM Prompting in the detailed arXiv paper: [here](https://arxiv.org/abs/2310.11441).

For this initial version, a simple YOLOv8 model is trained for button detection, and the `best.pt` file is included under `model/weights/`. Users are encouraged to swap in their `best.pt` file to evaluate performance improvements. If your model outperforms the existing one, please contribute by creating a pull request (PR).

Start `operate` with the SoM model

```
operate -m gpt-4-with-som
```


## Compatibility
- This project is compatible with Mac OS, Windows, and Linux (with X server installed).

## OpenAI Rate Limiting Note
The ```gpt-4-vision-preview``` model is required. To unlock access to this model, your account needs to spend at least \$5 in API credits. Pre-paying for these credits will unlock access if you haven't already spent the minimum \$5.   
Learn more **[here](https://platform.openai.com/docs/guides/rate-limits?context=tier-one)**
