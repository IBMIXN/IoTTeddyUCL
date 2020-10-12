# node-red-contrib-stt-utils
This is a collection of nodes for localised audio processing and speech to text in Node-RED, adapting existing Node.js modules for the platform. The nodes are summarised here, but more detailed documentation is available within the Node-RED documentation system.

## Installation
This package is installed as a npm package, to install it download the package then run `npm install` within the package folder, then run `npm install filepath` inside your Node-RED folder in your user area, where filepath is the file path to the package folder.

## wav-decode
This node adapts the node-wav module to Node-RED, it accepts a buffer containing a wav file, and outputs a message containing the audio data of the file in the payload, and formatting information as a object on the format property of the message.

## pcm-format
The node adapts the pcm-format module to Node-RED, it accepts buffers containing PCM audio of 16-bit or 32-bit, signed or unsigned, integer audio, and 32-bit float audio. The configuration options specific the input and output formats of the audio.

## pcm-resample
This node adapts the speex-resampler module to Node-RED, it accepts buffers containing 16-bit signed integer PCM audio, and outputs the same audio resampled. The input and output sample rate, as well as the quality of the resampling, is specified in the edit dialog for this node.

## node-vad
This node adapts the Node-VAD module to Node-RED, it accepts buffers containing 16-bit signed integer PCM audio, and outputs a series of audio frames containing speech. Whenever a particular utterance ends, the last frame of the utterance is marked with the complete property, for compatibility with join nodes and the stt node. The aggressiveness of the filtering and the sample rate of input audio can be configured in the edit dialog.

## stt
This node adapts the Node.JS API for the Mozilla DeepSpeech Speech-To-Text engine. This requires an external model and scorer file which is available [here.](https://github.com/mozilla/DeepSpeech/releases/latest) For Windows the model file needed is the .pbmm file, and for a Raspberry Pi the model file is the .tflite file.
