# Reference

* [Supported Languages](#supported-languages)
* [MQTT API](#mqtt-api)
* [HTTP API](#http-api)
* [Websocket API](#websocket-api)
* [Profile Settings](#profile-settings)
* [Command Line](#command-line)

## Supported Languages

The table below lists which components and compatible with Rhasspy's supported languages.

| Category               | Name                                           | Offline?               | en       | de       | es       | fr       | it       | nl       | ru       | el       | hi       | zh       | vi       | pt       | sv       | ca       |
| --------               | ------                                         | --------               | -------  | -------  | -------  | -------  | -------  | -------  | -------  | -------  | -------  | -------  | -------  | -------  | -------  | -------  |
| **Wake Word**          | [pocketsphinx](wake-word.md#pocketsphinx)      | &#x2713;               | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; |          |          |          |          |
|                        | [porcupine](wake-word.md#porcupine)            | &#x2713;               | &#x2713; |          |          |          |          |          |          |          |          |          |          |          |          |          |
|                        | [snowboy](wake-word.md#snowboy)                | *requires account*     | &#x2713; | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   |
|                        | [precise](wake-word.md#mycroft-precise)        | &#x2713;               | &#x2713; | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   | &bull;   |
| **Speech to Text**     | [pocketsphinx](speech-to-text.md#pocketsphinx) | &#x2713;               | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; |          | &#x2713; |          | &#x2713; |
|                        | [kaldi](speech-to-text.md#kaldi)               | &#x2713;               | &#x2713; | &#x2713; |          | &#x2713; |          | &#x2713; |          |          |          |          | &#x2713; |          | &#x2713; |          |
| **Intent Recognition** | [fsticuffs](intent-recognition.md#fsticuffs)   | &#x2713;               | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; |
|                        | [fuzzywuzzy](intent-recognition.md#fuzzywuzzy) | &#x2713;               | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; |
|                        | [adapt](intent-recognition.md#mycroft-adapt)   | &#x2713;               | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; |
|                        | [flair](intent-recognition.md#flair)           | &#x2713;               | &#x2713; | &#x2713; | &#x2713; | &#x2713; |          | &#x2713; |          |          |          |          |          | &#x2713; |          | &#x2713; |
|                        | [rasaNLU](intent-recognition.md#rasanlu)       | *needs extra software* | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; |
| **Text to Speech**     | [espeak](text-to-speech.md#espeak)             | &#x2713;               | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; |
|                        | [flite](text-to-speech.md#flite)               | &#x2713;               | &#x2713; |          |          |          |          |          |          |          | &#x2713; |          |          |          |          |          |
|                        | [picotts](text-to-speech.md#picotts)           | &#x2713;               | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; |          |          |          |          |          |          |          |          |          |
|                        | [marytts](text-to-speech.md#marytts)           | &#x2713;               | &#x2713; | &#x2713; |          | &#x2713; | &#x2713; |          | &#x2713; |          |          |          |          |          |          |          |
|                        | [wavenet](text-to-speech.md#google-wavenet)    |                        | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; |          | &#x2713; | &#x2713; |          | &#x2713; | &#x2713; |          |

&bull; - yes, but requires training/customization

## MQTT API

Rhasspy implements a superset of the [Hermes protocol](https://docs.snips.ai/reference/hermes) in [rhasspy-hermes](https://github.com/rhasspy/rhasspy-hermes) for the following components:

* [Audio Server](#audio-server)
* [Automated Speech Recognition](#automated-speech-recognition)
* [Dialogue Manager](#dialogue-manager)
* [Grapheme to Phoneme](#grapheme-to-phoneme)
* [Hotword Detection](#hotword-detection)
* [Intent Handling](#intent-handling)
* [Natural Language Understanding](#natural-language-understanding)
* [Text to Speech](#text-to-speech)

### Audio Server

Messages for [audio input](audio-input.md) and [audio output](audio-output.md).

* <a id="audioserver_audioframe"><tt>hermes/audioServer/&lt;siteId&gt;/audioFrame</tt></a> (binary)
    * Chunk of WAV audio data
    * `wav_bytes: bytes` - WAV data to play (**message payload**)
    * `siteId: string` - Hermes site ID (part of topic)
* <a id="audioserver_playbytes"><tt>hermes/audioServer/&lt;siteId&gt;/playBytes/&lt;requestId&gt;</tt></a> (JSON)
    * Play WAV data
    * `wav_bytes: bytes` - WAV data to play (message payload)
    * `requestId: string` - unique ID for request (part of topic)
    * `siteId: string` - Hermes site ID (part of topic)
    * Response(s)
        * [`hermes/audioServer/<siteId>/playFinished`](#audioserver_playfinished) (JSON)
* <a id="audioserver_playfinished"><tt>hermes/audioServer/&lt;siteId&gt;/playFinished</tt></a>
    * Indicates that audio has finished playing
    * Response to [`hermes/audioServer/<siteId>/playBytes/<requestId>`](#audioserver_playbytes)
    * `siteId: string` - Hermes site ID (part of topic)
    * `id: string = ""` - `requestId` from request message
    
### Automated Speech Recognition

Messages for [speech to text](speech-to-text.md).

* <a id="asr_toggleon"><tt>hermes/asr/toggleOn</tt></a> (JSON)
    * Enables ASR system
    * `siteId: string = "default"` - Hermes site ID
* <a id="asr_toggleoff"><tt>hermes/asr/toggleOff</tt></a> (JSON)
    * Disables ASR system
    * `siteId: string = "default"` - Hermes site ID
* <a id="asr_startlistening"><tt>hermes/asr/startListening</tt></a> (JSON)
    * Tell ASR system to start recording/transcribing
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
* <a id="asr_stoplistening"><tt>hermes/asr/stopListening</tt></a> (JSON)
    * Tell ASR system to stop recording
    * Emits [`textCaptured`](#asr_textcaptured) if silence has was not detected earlier
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
* <a id="asr_textcaptured"><tt>hermes/asr/textCaptured</tt></a> (JSON)
    * Successful transcription, sent either when silence is detected or on [`stopListening`](#asr_stoplistening)
    * `text: string` - transcription text
    * `likelihood: float` - confidence from ASR system
    * `seconds: float` - transcription time in seconds
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
* <a id="asr_error"><tt>hermes/error/asr</tt></a> (JSON)
    * Sent when an error occurs in the ASR system
    * `error: string` - description of the error
    * `context: string` - system-defined context of the error
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
* <a id="asr_train"><tt>rhasspy/asr/&lt;siteId&gt;/train</tt></a> (JSON, Rhasspy only)
    * Instructs the ASR system to re-train
    * `id: string` - unique ID for request (copied to [`trainSuccess`](#asr_trainsuccess))
    * `graph_dict: object` - intent graph from [rhasspy-nlu](https://github.com/rhasspy/rhasspy-nlu) encoded as a JSON object
    * `siteId: string` - Hermes site ID (part of topic)
    * Response(s)
        * [`rhasspy/asr/<siteId>/trainSuccess`](#asr_trainsuccess)
        * [`hermes/error/asr`](#asr_error)
* <a id="asr_trainsuccess"><tt>rhasspy/asr/&lt;siteId&gt;/trainSuccess</tt></a> (JSON, Rhasspy only)
    * Indicates that training was successful
    * `id: string` - unique ID from request (copied from [`train`](#asr_train))
    * `siteId: string` - Hermes site ID (part of topic)
    * Response to [`rhasspy/asr/<siteId>/train`](#asr_train)
* <a id="asr_audiocaptured"><tt>rhasspy/asr/&lt;siteId&gt;/&lt;sessionId&gt;/audioCaptured</tt></a> (binary, Rhasspy only)
    * WAV audio data captured by ASR session
    * `siteId: string` - Hermes site ID (part of topic)
    * `sessionId: string` - current session ID (part of topic)
    * Only sent if `sendAudioCaptured = true` in [`startListening`](#asr_startlistening)
    
### Dialogue Manager

Messages for managing dialogue sessions. These can be initiated by a hotword [`detected`](#hotword_detected) message (or [`/api/listen-for-command`](#api_listen_for_command)), and manually with a [`startSession`](#dialoguemanager_startsession) message (or [`/api/start-recording`](#api_start_recording)).

* <a id="dialoguemanager_startsession"><tt>hermes/dialogueManager/startSession</tt></a> (JSON)
    * Starts a new dialogue session (done automatically on hotword [`detected`](#hotword_detected))
    * `init: object` - JSON object with one of two forms:
        * Action
            * `type: string = "action"` - required
            * `canBeEnqueued: bool` - true if session can be queued if there is already one (required)
            * `text: string = ""` - sentence to speak using [text to speech](#text-to-speech)
            * `intentFilter: [string] = null` - valid intent names (`null` means all) 
            * `sendIntentNotRecognized: bool = false` - send [`hermes/dialogueManager/intentNotRecognized`](#dialoguemanager_intentnotrecognized) if [intent recognition](intent-recognition.md) fails
        * Notification
            * `type: string = "notification"` - required
            * `text: string` - sentence to speak using [text to speech](#text-to-speech) (required)
    * `siteId: string = "default"` - Hermes site ID
    * `customData: string = ""` - user-defined data passed to subsequent session messages
    * Response(s)
        * [`hermes/dialogueManager/sessionStarted`](#dialoguemanager_sessionstarted)
        * [`hermes/dialogueManager/sessionQueued`](#dialoguemanager_sessionqueued)
* <a id="dialoguemanager_sessionstarted"><tt>hermes/dialogueManager/sessionStarted</tt></a> (JSON)
    * Indicates a session has started
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    * `customData: string = ""` - user-defined data (copied from [`startSession`](#dialoguemanager_startsession))
    * Response to [`hermes/dialogueManager/startSession`]
* <a id="dialoguemanager_sessionqueued"><tt>hermes/dialogueManager/sessionQueued</tt></a> (JSON)
    * Indicates a session has been queued (only when `init.canBeEnqueued = true` in [`startSession`](#dialoguemanager_startsession))
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    * `customData: string = ""` - user-defined data (copied from [`startSession`](#dialoguemanager_startsession))
    * Response to [`hermes/dialogueManager/startSession`]
* <a id="dialoguemanager_continuesession"><tt>hermes/dialogueManager/continueSession</tt></a> (JSON)
    * Requests that a session be continued after an [`intent`](#nlu_intent) has been recognized
    * `sessionId: string` - current session ID (required)
    * `customData: string = ""` - user-defined data (overrides session `customData` if not empty)
    * `text: string = ""` - sentence to speak using [text to speech](#text-to-speech)
    * `intentFilter: [string] = null` - valid intent names (`null` means all) 
    * `sendIntentNotRecognized: bool = false` - send [`hermes/dialogueManager/intentNotRecognized`](#dialoguemanager_intentnotrecognized) if [intent recognition](intent-recognition.md) fails
* <a id="dialoguemanager_endsession"><tt>hermes/dialogueManager/endSession</tt></a> (JSON)
    * Requests that a session be terminated nominally
    * `sessionId: string` - current session ID (required)
    * `customData: string = ""` - user-defined data (overrides session `customData` if not empty)
* <a id="dialoguemanager_sessionended"><tt>hermes/dialogueManager/sessionEnded</tt></a> (JSON)
    * Indicates a session has terminated
    * `termination: string` reason for termination (required), one of:
        * nominal
        * abortedByUser
        * intentNotRecognized
        * timeout
        * error
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    * `customData: string = ""` - user-defined data (copied from [`startSession`](#dialoguemanager_startsession))
    * Response to [`hermes/dialogueManager/endSession`](#dialoguemanager_endsession) or other reasons for a session termination
* <a id="dialoguemanager_intentnotrecognized"><tt>hermes/dialogueManager/intentNotRecognized</tt></a> (JSON)
    * Sent when [intent recognition](intent-recognition.md) fails during a session (only when `init.sendIntentNotRecognized = true` in [`startSession`](#dialoguemanager_startsession))
    * `input: string` input to NLU system (required)
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    * `customData: string = ""` - user-defined data (copied from [`startSession`](#dialoguemanager_startsession))

### Grapheme to Phoneme

Messages for looking up [word pronunciations](training.md#custom-words). See also the [`/api/lookup`](#api_lookup) HTTP endpoint.

Words are usually looked up from a [phonetic dictionary](https://cmusphinx.github.io/wiki/tutorialdict/) included with the ASR system. The current [speech to text](services.md#speech-to-text) services handle these messages.

* <a id="g2p_pronounce"><tt>rhasspy/g2p/pronounce</tt></a> (JSON, Rhasspy only)
    * Requests phonetic pronunciations of words
    * `id: string = ""` - unique ID for request (copied to [`phonemes`](#g2p_phonemes))
    * `words: [string]` - words to pronounce (required)
    * `numGuesses: int = 5` - number of guesses if not in dictionary
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    * Response(s)
        * [`rhasspy/g2p/phonemes`](#g2p_phonemes)
* <a id="g2p_phonemes"><tt>rhasspy/g2p/phonemes</tt></a> (JSON, Rhasspy only)
    * Phonetic pronunciations of words, either from a dictionary or grapheme-to-phoneme model
    * `wordPhonemes: [object]` - phonetic pronunciations (required), keyed by word, values are:
        * `phonemes: [string]` - phonemes for word (key)
        * `guessed: bool` - true if pronunciation came from a grapheme-to-phoneme model
    * `id: string = ""` - unique ID for request (copied from [`pronounce`](#g2p_pronounce))
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    * Response to [`rhasspy/g2p/pronounce`](#g2p_pronounce)
* <a id="g2p_error"><tt>rhasspy/error/g2p</tt></a> (JSON, Rhasspy only)
    * Sent when an error occurs in the G2P system
    * `error: string` - description of the error
    * `context: string` - system-defined context of the error
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    
### Hotword Detection

Messages for [wake word detection](wake-word.md). See also the [`/api/listen-for-wake`](#api_listen_for_wake) HTTP endpoint and the [`/api/events/wake`](#api_events_wake) Websocket endpoint.

* <a id="hotword_toggleon"><tt>hermes/hotword/toggleOn</tt></a> (JSON)
    * Enables hotword detection
    * `siteId: string = "default"` - Hermes site ID
* <a id="hotword_toggleoff"><tt>hermes/hotword/toggleOff</tt></a> (JSON)
    * Disables hotword detection
    * `siteId: string = "default"` - Hermes site ID
* <a id="hotword_detected"><tt>hermes/hotword/&lt;wakewordId&gt;/detected</tt></a> (JSON)
    * Indicates a hotword was successfully detected
    * `wakewordId: string` - wake word ID (part of topic)
    * `modelId: string` - ID of wake word model used (service specific)
    * `modelVersion: string = ""` - version of wake word model used (service specific)
    * `modelType: string = "personal"` - type of wake word model used (service specific)
    * `currentSensitivity: float = 1.0` - sensitivity of wake word detection (service specific)
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID (Rhasspy only)
* <a id="hotword_error"><tt>hermes/error/hotword</tt></a> (JSON, Rhasspy only)
    * Sent when an error occurs in the hotword system
    * `error: string` - description of the error
    * `context: string` - system-defined context of the error
    * `siteId: string = "default"` - Hermes site ID

### Intent Handling

Messages for [intent handling](intent-handling.md).

* <a id="handle_toggleon"><tt>rhasspy/handle/toggleOn</tt></a> (JSON, Rhasspy only)
    * Enables intent handling
    * `siteId: string = "default"` - Hermes site ID
* <a id="handle_toggleoff"><tt>rhasspy/handle/toggleOff</tt></a> (JSON, Rhasspy only)
    * Disables intent handling
    * `siteId: string = "default"` - Hermes site ID

### Natural Language Understanding

* <a id="nlu_query"><tt>hermes/nlu/query</tt></a> (JSON)
    * Request an intent to be recognized from text
    * `input: string` - text to recognize intent from (required)
    * `intentFilter: [string] = null` - valid intent names (`null` means all) 
    * `id: string = ""` - unique id for request (copied to response messages)
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    * Response(s)
        * [`hermes/nlu/intent/<intentName>`](#nlu_intent)
        * [`hermes/nlu/intentNotRecognized`](#nlu_intentnotrecognized)
* <a id="nlu_intent"><tt>hermes/nlu/intent/&lt;intentName&gt;</tt></a> (JSON)
    * Sent when an intent was successfully recognized
    * `input: string` - text from query (required)
    * `intent: object` - details of recognized intent (required)
        * `intentName: string` - name of intent (required)
        * `confidenceScore: float` - confidence from NLU system for this intent (required)
    * `slots: [object] = []` - details of named entities, list of:
        * `entity: string` - name of entity (required)
        * `slotName: string` - name of slot (required)
        * `confidence: float` - confidence from NLU system for this slot (required)
        * `raw_value: string` - entity value **without** [substitutons](training.md#substitutions) (required)
        * `value: string` - entity value with [substitutons](training.md#substitutions) (required)
        * `range: object = null` - indexes of entity value in text
            * `start: int` - start index
            * `end: int` - end index (exclusive)
    * `id: string = ""` - unique id for request (copied from [`query`](#nlu_query))
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    * `customData: string = ""` - user-defined data (copied from [`startSession`](#dialoguemanager_startsession))
    * `asrTokens: [string] = []` - tokens from [transcription](#asr_textcaptured)
    * `asrConfidence: float = 1.0` - confidence from ASR system for input text
    * Response to [`hermes/nlu/query`](#nlu_query)
* <a id="nlu_intentnotrecognized"><tt>hermes/nlu/intentNotRecognized</tt></a> (JSON)
    * Sent when [intent recognition](intent-recognition.md) fails
    * `input: string` - text from query (required)
    * `id: string = ""` - unique id for request (copied from [`query`](#nlu_query))
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    * Response to [`hermes/nlu/query`](#nlu_query)
* <a id="nlu_error"><tt>hermes/error/nlu</tt></a> (JSON)
    * Sent when an error occurs in the NLU system
    * `error: string` - description of the error
    * `context: string` - system-defined context of the error
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
* <a id="nlu_train"><tt>rhasspy/nlu/&lt;siteId&gt;/train</tt></a> (JSON, Rhasspy only)
    * Instructs the NLU system to re-train
    * `id: string` - unique ID for request (copied to [`trainSuccess`](#nlu_trainsuccess))
    * `graph_dict: object` - intent graph from [rhasspy-nlu](https://github.com/rhasspy/rhasspy-nlu) encoded as a JSON object
    * `siteId: string` - Hermes site ID (part of topic)
    * Response(s)
        * [`rhasspy/nlu/<siteId>/trainSuccess`](#nlu_trainsuccess)
        * [`hermes/error/nlu`](#nlu_error)
* <a id="nlu_trainsuccess"><tt>rhasspy/nlu/&lt;siteId&gt;/trainSuccess</tt></a> (JSON, Rhasspy only)
    * Indicates that training was successful
    * `id: string` - unique ID from request (copied from [`train`](#nlu_train))
    * `siteId: string` - Hermes site ID (part of topic)
    * Response to [`rhasspy/nlu/<siteId>/train`](#nlu_train)
    
### Text to Speech

* <a id="tts_say"><tt>hermes/tts/say</tt></a> (JSON)
    * Generate spoken audio for a sentence using the configured text to speech system
    * Automatically sends [`playBytes`](#audioserver_playbytes)
        * `playBytes.requestId = say.id`
    * `text: string` - sentence to speak (required)
    * `lang: string = ""` - language for TTS system
    * `id: string = ""` - unique ID for request (copied to `sayFinished`)
    * `siteId: string = "default"` - Hermes site ID
    * `sessionId: string = ""` - current session ID
    * Response(s)
        * [`hermes/tts/sayFinished`](#tts_sayfinished) (JSON)
* <a id="tts_sayfinished"><tt>hermes/tts/sayFinished</tt></a> (JSON)
    * Indicates that the text to speech system has finished generating audio
    * `id: string = ""` - unique ID for request (copied from `say`)
    * `siteId: string = "default"` - Hermes site ID
    * Response to [`hermes/tts/say`](#tts_say)
    * Listen for [`playFinished`](#audioserver_playfinished) to determine when audio is finished playing
        * `playFinished.id = sayFinished.id`

## HTTP API

Rhasspy's HTTP endpoints are documented below. You can also visit `/api/` in your Rhasspy server (note the final slash) to try out each endpoint.

Application authors may want to use the [rhasspy-client](https://pypi.org/project/rhasspy-client/), which provides a high-level interface to a remote Rhasspy server.

### Endpoints

* <a id="api_custom_words"><tt>/api/custom-words</tt></a>
    * GET custom word dictionary as plain text, or POST to overwrite it
    * See `custom_words.txt` in your profile directory
* `/api/download-profile`
    * Force Rhasspy to re-download profile
* <a id="api_listen_for_command"><tt>/api/listen-for-command</tt></a>
    * POST to wake Rhasspy up and start listening for a voice command
    * Returns intent JSON when command is finished
    * `?nohass=true` - stop Rhasspy from handling the intent
    * `?timeout=<seconds>` - override default command timeout
    * `?entity=<entity>&value=<value>` - set custom entity/value in recognized intent
* <a id="api_listen_for_wake"><tt>/api/listen-for-wake</tt></a>
    * POST "on" to have Rhasspy listen for a wake word
    * POST "off" to disable wake word
* <a id="api_lookup"><tt>/api/lookup</tt></a>
    * POST word as plain text to look up or guess pronunciation
    * `?n=<number>` - return at most `n` guessed pronunciations
* <a id="/api/microphones"><tt>/api/microphones</tt></a>
    * GET list of available microphones
* <a id="api_phonemes"><tt>/api/phonemes</tt></a>
    * GET example phonemes from speech recognizer for your profile
    * See `phoneme_examples.txt` in your profile directory
* <a id="api_play_wav"><tt>/api/play-wav</tt></a>
    * POST to play WAV data
* <a id="api_profile"><tt>/api/profile</tt></a>
    * GET the JSON for your profile, or POST to overwrite it
    * `?layers=profile` to only see settings different from `defaults.json`
    * See `profile.json` in your profile directory
* <a id="api_restart"><tt>/api/restart</tt></a>
    * Restart Rhasspy server
* <a id="api_sentences"><tt>/api/sentences</tt></a>
    * GET voice command templates or POST to overwrite
    * Set `Accept: application/json` to GET JSON with all sentence files
    * Set `Content-Type: application/json` to POST JSON with sentences for multiple files
    * See `sentences.ini` and `intents` directory in your profile
* <a id="api_slots"><tt>/api/slots</tt></a>
    * GET slot values as JSON or POST to add to/overwrite them
    * `?overwrite_all=true` to clear slots in JSON before writing
* <a id="api_speakers"><tt>/api/speakers</tt></a>
    * GET list of available audio output devices
* <a id="api_speech_to_intent"><tt>/api/speech-to-intent</tt></a>
    * POST a WAV file and have Rhasspy process it as a voice command
    * Returns intent JSON when command is finished
    * `?nohass=true` - stop Rhasspy from handling the intent
* <a id="api_speech_to_text"><tt>/api/speech-to-text</tt></a>
    * POST a WAV file and have Rhasspy return the text transcription
    * Set `Accept: application/json` to receive JSON with more details
    * `?noheader=true` - send raw 16-bit 16Khz mono audio without a WAV header
* <a id="api_start_recording"><tt>/api/start-recording</tt></a>
    * POST to have Rhasspy start recording a voice command
* <a id="api_stop_recording"><tt>/api/stop-recording</tt></a>
    * POST to have Rhasspy stop recording and process recorded data as a voice command
    * Returns intent JSON when command has been processed
    * `?nohass=true` - stop Rhasspy from handling the intent
* <a id="api_test_microphones"><tt>/api/test-microphones</tt></a>
    * GET list of available microphones and if they're working
* <a id="api_text_to_intent"><tt>/api/text-to-intent</tt></a>
    * POST text and have Rhasspy process it as command
    * Returns intent JSON when command has been processed
    * `?nohass=true` - stop Rhasspy from handling the intent
* <a id="api_text_to_speech"><tt>/api/text-to-speech</tt></a>
    * POST text and have Rhasspy speak it
    * `?play=false` - get WAV data instead of having Rhasspy speak
    * `?voice=<voice>` - override default TTS voice
    * `?language=<language>` - override default TTS language or locale
    * `?repeat=true` - have Rhasspy repeat the last sentence it spoke
* <a id="api_train"><tt>/api/train</tt></a>
    * POST to re-train your profile
* <a id="api_unknown_words"><tt>/api/unknown-words</tt></a>
    * GET words that Rhasspy doesn't know in your sentences
    * See `unknown_words.txt` in your profile directory
* <a id="api_mqtt"><tt>/api/mqtt</tt></a>
    * POST JSON payload to `/api/mqtt/your/full/topic`
    * Payload will be published to `your/full/topic`

## Websocket API

* <a id="api_events_intent"><tt>/api/events/intent</tt></a>
    * Emits [JSON-encoded intents](usage.md#websocket-intents) after each NLU [query](#nlu_query)
* <a id="api_events_text"><tt>/api/events/text</tt></a>
    * Emits [JSON-encoded transcriptions](usage.md#websocket-transcriptions) after each ASR [transcription](#asr_textcaptured)
* <a id="api_events_wake"><tt>/api/events/wake</tt></a>
    * Emits [JSON-encoded detections](usage.md#websocket-wake) after each wake word [detection](#hotword_detected)
* <a id="api_mqtt"><tt>/api/mqtt</tt></a>
    * Allows you to subscribe to, receive, and publish [JSON-encoded MQTT messages](usage.md#websocket-mqtt-messages)

## Profile Settings

All available profile sections and settings are listed below:

* `home_assistant` - how to communicate with Home Assistant/Hass.io
    * `url` - Base URL of Home Assistant server (no `/api`)
    * `access_token` -  long-lived access token for Home Assistant (Hass.io token is used automatically)
    * `api_password` - Password, if you have that enabled (deprecated)
    * `pem_file` - Full path to your <a href="http://docs.python-requests.org/en/latest/user/advanced/#ssl-cert-verification">CA_BUNDLE file or a directory with certificates of trusted CAs</a>
    * `event_type_format` - Python format string used to create event type from intent type (`{0}`)
* `speech_to_text` - transcribing [voice commands to text](speech-to-text.md)
    * `system` - name of speech to text system (`pocketsphinx`, `kaldi`, `remote`, `command`, or `dummy`)
    * `pocketsphinx` - configuration for [Pocketsphinx](speech-to-text.md#pocketsphinx)
        * `compatible` - true if profile can use pocketsphinx for speech recognition
        * `acoustic_model` - directory with CMU 16 kHz acoustic model
        * `base_dictionary` - large text file with word pronunciations (read only)
        * `custom_words` - small text file with words/pronunciations added by user
        * `dictionary` - text file with all words/pronunciations needed for example sentences
        * `unknown_words` - small text file with guessed word pronunciations (from phonetisaurus)
        * `language_model` - text file with trigram [ARPA language model](https://cmusphinx.github.io/wiki/arpaformat/) built from example sentences
        * `open_transcription` - true if general language model should be used (custom voices commands ignored)
        * `base_language_model` - large general language model (read only)
        * `mllr_matrix` - MLLR matrix from [acoustic model tuning](https://cmusphinx.github.io/wiki/tutorialtuning/)
        * `mix_weight` - how much of the base language model to [mix in during training](training.md#language-model-mixing) (0-1)
    * `kaldi` - configuration for [Kaldi](speech-to-text.md#kaldi)
        * `compatible` - true if profile can use Kaldi for speech recognition
        * `kaldi_dir` - absolute path to Kaldi root directory
        * `model_dir` - directory where Kaldi model is stored (relative to profile directory)
        * `graph` - directory where HCLG.fst is located (relative to `model_dir`)
        * `base_graph` - directory where large general HCLG.fst is located (relative to `model_dir`)
        * `base_dictionary` - large text file with word pronunciations (read only)
        * `custom_words` - small text file with words/pronunciations added by user
        * `dictionary` - text file with all words/pronunciations needed for example sentences
        * `open_transcription` - true if general language model should be used (custom voices commands ignored)
        * `unknown_words` - small text file with guessed word pronunciations (from phonetisaurus)
        * `mix_weight` - how much of the base language model to [mix in during training](training.md#language-model-mixing) (0-1)
    * `remote` - configuration for [remote Rhasspy server](speech-to-text.md#remote-http-server)
        * `url` - URL to POST WAV data for transcription (e.g., `http://your-rhasspy-server:12101/api/speech-to-text`)
    * `command` - configuration for [external speech-to-text program](speech-to-text.md#command)
        * `program` - path to executable
        * `arguments` - list of arguments to pass to program
    * `sentences_ini` - Ini file with example [sentences/JSGF templates](training.md#sentencesini) grouped by intent
    * `sentences_dir` - Directory with additional sentence templates (default: `intents`)
    * `g2p_model` - finite-state transducer for phonetisaurus to guess word pronunciations
    * `g2p_casing` - casing to force for g2p model (`upper`, `lower`, or blank)
    * `dictionary_casing` - casing to force for dictionary words (`upper`, `lower`, or blank)
    * `slots_dir` - directory to look for [slots lists](training.md#slots-lists) (default: `slots`)
    * `slot_programs` - directory to look for [slot programs](training.md#slot-programs) (default `slot_programs`)
* `intent` - transforming text commands to intents
    * `system` - intent recognition system (`fsticuffs`, `fuzzywuzzy`, `rasa`, `remote`, `adapt`, `command`, or `dummy`)
    * `fsticuffs` - configuration for [OpenFST-based](https://www.openfst.org) intent recognizer
        * `intent_json` - path to intent graph JSON file generated by [rhasspy-nlu][https://github.com/rhasspy/rhasspy-nlu]
        * `converters_dir` - directory to look for [converter](training.md#converters) programs (default: `converters`)
        * `ignore_unknown_words` - true if words not in the FST symbol table should be ignored
        * `fuzzy` - true if text is matching in a fuzzy manner, skipping words in `stop_words.txt`
    * `fuzzywuzzy` - configuration for simplistic [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance) based intent recognizer
        * `examples_json` - JSON file with intents/example sentences
        * `min_confidence` - minimum confidence required for intent to be converted to a JSON event (0-1)
    * `remote` - configuration for remote Rhasspy server
        * `url` - URL to POST text to for intent recognition (e.g., `http://your-rhasspy-server:12101/api/text-to-intent`)
    * `rasa` - configuration for [Rasa NLU](https://rasa.com/) based intent recognizer
        * `url` - URL of remote Rasa NLU server (e.g., `http://localhost:5005/`)
        * `examples_markdown` - Markdown file to generate with intents/example sentences
        * `project_name` - name of project to generate during training
    * `adapt` - configuration for [Mycroft Adapt](https://github.com/MycroftAI/adapt) based intent recognizer
        * `stop_words` - text file with words to ignore in training sentences
    * `command` - configuration for external speech-to-text program
        * `program` - path to executable
        * `arguments` - list of arguments to pass to program
    * `replace_numbers` if true, automatically replace number ranges (`N..M`) or numbers (`N`) with words
* `text_to_speech` - pronouncing words
    * `system` - text to speech system (`espeak`, `flite`, `picotts`, `marytts`, `command`, or `dummy`)
    * `espeak` - configuration for [eSpeak](http://espeak.sourceforge.net)
        * `phoneme_map` - text file mapping CMU phonemes to eSpeak phonemes
    * `flite` - configuration for [flite](http://www.festvox.org/flite)
        * `voice` - name of voice to use (e.g., `kal16`, `rms`, `awb`)
    * `picotts` - configuration for [PicoTTS](https://en.wikipedia.org/wiki/SVOX)
        * `language` - language to use (default if not present)
    * `marytts` - configuration for [MaryTTS](http://mary.dfki.de)
        * `url` - address:port of MaryTTS server (port is usually 59125)
        * `voice` - name of voice to use (e.g., `cmu-slt`). Default if not present.
        * `locale` - name of locale to use (e.g., `en-US`). Default if not present.
    * `wavenet` - configuration for Google's [WaveNet](https://cloud.google.com/text-to-speech/docs/wavenet)
        * `cache_dir` - path to directory in your profile where WAV files are cached
        * `credentials_json` - path to the JSON credentials file (generated online)
        * `gender` - gender of speaker (`MALE` `FEMALE`)
        * `language_code` - language/locale e.g. `en-US`,
        * `sample_rate` - WAV sample rate (default: 22050)
        * `url` - URL of WaveNet endpoint
        * `voice` - voice to use (e.g., `Wavenet-C`)
        * `fallback_tts` - text to speech system to use when offline or error occurs (e.g., `espeak`)
    * `phoneme_examples` - text file with examples for each CMU phoneme
* `training` - training speech/intent recognizers
    * `speech_to_text` - training for speech decoder
        * `system` - speech to text training system (`auto` or `dummy`)
        * `command` - configuration for external speech-to-text training program
            * `program` - path to executable
            * `arguments` - list of arguments to pass to program
        * `remote` - configuration for external HTTP endpoint
            * `url` - URL of speech to text training endpoint
    * `intent` - training for intent recognizer
        * `system` - intent recognizer training system (`auto` or `dummy`)
        * `command` - configuration for external intent recognizer training program
            * `program` - path to executable
            * `arguments` - list of arguments to pass to program
        * `remote` - configuration for external HTTP endpoint
            * `url` - URL of intent recognizer training endpoint
* `wake` - waking Rhasspy up for speech input
    * `system` - wake word recognition system (`pocketsphinx`, `snowboy`, `precise`, `porcupine`, `command`, or `dummy`)
    * `pocketsphinx` - configuration for Pocketsphinx wake word recognizer
        * `keyphrase` - phrase to wake up on (3-4 syllables recommended)
        * `threshold` - sensitivity of detection (recommended range 1e-50 to 1e-5)
        * `chunk_size` - number of bytes per chunk to feed to Pocketsphinx (default 960)
    * `snowboy` - configuration for [snowboy](https://snowboy.kitt.ai)
        * `model` - path to model file(s), separated by commas (in profile directory)
        * `sensitivity` - model sensitivity (0-1, default 0.5)
        * `audio_gain` - audio gain (default 1)
        * `apply_frontend` - true if ApplyFrontend should be set
        * `chunk_size` - number of bytes per chunk to feed to snowboy (default 960)
        * `model_settings` - settings for each snowboy model path (e.g., `snowboy/snowboy.umdl`)
            * `<MODEL_PATH>`
                * `sensitivity` - model sensitivity
                * `audio_gain` - audio gain
                * `apply_frontend` - true if ApplyFrontend should be set
    * `precise` - configuration for [Mycroft Precise](https://github.com/MycroftAI/mycroft-precise)
        * `engine_path` - path to the precise-engine binary
        * `model` - path to model file (in profile directory)
        * `sensitivity` - model sensitivity (0-1, default 0.5)
        * `trigger_level`  - number of events to trigger activation (default 3)
        * `chunk_size` - number of bytes per chunk to feed to Precise (default 2048)
    * `porcupine` - configuration for [PicoVoice's Porcupine](https://github.com/Picovoice/Porcupine)
        * `library_path` - path to  `libpv_porcupine.so` for your platform/architecture
        * `model_path` - path to the `porcupine_params.pv` (lib/common)
        * `keyword_path` - path to the `.ppn` keyword file
        * `sensitivity` - model sensitivity (0-1, default 0.5)
    * `command` - configuration for external speech-to-text program
        * `program` - path to executable
        * `arguments` - list of arguments to pass to program
* `microphone` - configuration for audio recording
    * `system` - audio recording system (`pyaudio`, `arecord`, gstreamer`, or `dummy`)
    * `pyaudio` - configuration for [PyAudio](https://people.csail.mit.edu/hubert/pyaudio/) microphone
        * `device` - index of device to use or empty for default device
        * `frames_per_buffer` - number of frames to read at a time (default 480)
    * `arecord` - configuration for ALSA microphone
        * `device` - name of ALSA device (see `arecord -L`) to use or empty for default device
        * `chunk_size` - number of bytes to read at a time (default 960)
    * `gstreamer` - configuration for GStreamer audio recorder
        * `pipeline` - GStreamer pipeline (e.g., `FILTER ! FILTER ! ...`) without sink
* `sounds` - configuration for feedback sounds from Rhasspy
    * `system` - which sound output system to use (`aplay`, `command`, or `dummy`)
    * `wake` - path to WAV file to play when Rhasspy wakes up
    * `recorded` - path to WAV file to play when a command finishes recording
    * `aplay` - configuration for ALSA speakers
        * `device` - name of ALSA device (see `aplay -L`) to use or empty for default device
    * `command` - configuration for external audio output program
        * `program` - path to executable
        * `arguments` - list of arguments to pass to program
* `handle`
    * `system` - which intent handling system to use (`hass`, `command`, `remote`, or `dummy`)
    * `command` - configuration for external speech-to-text program
        * `program` - path to executable
        * `arguments` - list of arguments to pass to program
    * `remote` - configuration for remote HTTP intent handler
        * `url` - URL to POST intent JSON to and receive response JSON from
* `mqtt` - configuration for MQTT
    * `enabled` - true if external broker should be used (false uses internal broker)
    * `host` - external MQTT host
    * `port` - external MQTT port
    * `username` - external MQTT username (blank for anonymous)
    * `password` - external MQTT password
    * `site_id` - one or more Hermes site IDs (comma separated). First ID is used for new messages
* `download` - configuration for profile file downloading
    * `url_base` - base URL to download profile artifacts (defaults to Github)
    * `conditions` - profile settings that will trigger file downloads
        * keys are profile setting paths (e.g., `wake.system`)
        * values are dictionaries whose keys are profile settings values (e.g., `snowboy`)
            * settings may have the form `<=N` or `!X` to mean "less than or equal to N" or "not X"
            * leaf nodes are dictionaries whose keys are destination file paths and whose values reference the `files` dictionary
    * `files` - locations, etc. of files to download
        * keys are names of files
        * values are dictionaries with:
            * `url` - URL of file to download (appended to `url_base`)
            * `bytes_expected` - number of bytes file should be after decompression
            * `unzip` - `true` if file should be decompressed with `gunzip`
            * `parts` - list of objects representing parts of a file that should be combined with `cat`
                * `fragment` - fragment appended to file URL
                * `bytes_expected` - number of bytes for this part

## Command Line Tools

* `rhasspy-nlu`
* `rhasspy-hermes`
* `rhasspy-supervisor`