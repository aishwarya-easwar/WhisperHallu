# WhisperHallu
Experimental code: sound file preprocessing to optimize Whisper transcriptions without hallucinated texts

See this discussion: https://github.com/openai/whisper/discussions/679

# Algo
- remove silences, and normalize loudness.
- remove noise parts.
- add voice markers.
- apply speech compressor.
- try to transcribe. If markers are present in output, transcription is OK.
- if not, try to invert markers. If markers are present in output, transcription is OK.
- if not, try without markers.

# Complement

May be used to produce "accurate transcriptions" for WhisperTimeSync:<br/>
https://github.com/EtienneAb3d/WhisperTimeSync

May be tested using NeuroSpell Dictaphone:<br/>
https://neurospell.com/

# Code

```
from transcribeFasterWhisper import loadModel
from transcribeFasterWhisper import transcribePrompt

##### Need to be adapted for each language ####
lng="en"
prompt="Whisper, Ok. A pertinent sentence for your purpose in your language. Ok, Whisper. Whisper, Ok. Ok, Whisper. Whisper, Ok. Please find here, an unlikely ordinary sentence. This is to avoid a repetition to be deleted. Ok, Whisper. "
path="/your/path/to/sound/file"

loadModel("0")
result = transcribePrompt(path=path, lng=lng, prompt=prompt)
```
